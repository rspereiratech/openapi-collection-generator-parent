# OpenAPI Collection Generator

[![Build](https://github.com/rspereiratech/openapi-collection-generator-parent/actions/workflows/build.yml/badge.svg?branch=master)](https://github.com/rspereiratech/openapi-collection-generator-parent/actions/workflows/build.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
![Java 17+](https://img.shields.io/badge/Java-17%2B-blue)
![Maven 3.9+](https://img.shields.io/badge/Maven-3.9%2B-C71A36?logo=apachemaven&logoColor=white)
![OpenAPI 3.0](https://img.shields.io/badge/OpenAPI-3.0-6BA539?logo=openapiinitiative&logoColor=white)
![Swagger v3](https://img.shields.io/badge/Swagger-v3-85EA2D?logo=swagger&logoColor=black)
![Insomnia v4](https://img.shields.io/badge/Insomnia-v4-4000BF?logo=insomnia&logoColor=white)
![Status: Snapshot](https://img.shields.io/badge/Status-Snapshot-orange)
[![Donate](https://img.shields.io/badge/Donate-NOWPayments-1A1A1A?logo=bitcoin&logoColor=white)](https://nowpayments.io/donation/rspereiratech)

A Maven plugin that generates API client collections from OpenAPI specifications.

## Problem

Working with REST APIs often requires importing endpoints into tools like **Postman** or **Insomnia** for testing and development. Manually creating and maintaining these collections is tedious, error-prone, and quickly becomes outdated as APIs evolve.

## Solution

**OpenAPI Collection Generator** reads your OpenAPI (3.x) specification and automatically generates ready-to-import collection files for Postman and Insomnia. It integrates directly into the Maven build lifecycle, ensuring your collections are always in sync with your API definition.

### Features

- Generates **Postman v2.1** collections
- Generates **Insomnia v4** exports
- Supports generating **multiple formats** in a single execution
- Configurable **output directory** and **file naming pattern**
- Automatic **environment file** generation (e.g. server URLs)
- Runs during the `generate-resources` phase by default

## Module Structure

| Module | Description |
|---|---|
| `openapi-collection-generator-parent` | Parent POM with shared dependency management |
| `openapi-collection-generator-core` | Core library with generation orchestration, parsing, and writing |
| `openapi-collection-generator-postman` | Postman collection generator |
| `openapi-collection-generator-insomnia` | Insomnia collection generator |
| `openapi-collection-generator-maven-plugin` | Maven plugin (thin wrapper over core) |

## Usage

### 1. Add the plugin to your `pom.xml`

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.github.rspereiratech</groupId>
            <artifactId>openapi-collection-generator-maven-plugin</artifactId>
            <version>1.0.0-SNAPSHOT</version>
            <executions>
                <execution>
                    <goals>
                        <goal>generate</goal>
                    </goals>
                    <configuration>
                        <formats>
                            <format>POSTMAN</format>
                            <format>INSOMNIA</format>
                        </formats>
                        <collectionName>My_API</collectionName>
                    </configuration>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

### 2. Place your OpenAPI spec

By default, the plugin looks for the spec at:

```
src/main/resources/openapi.yaml
```

### 3. Run the build

```bash
mvn generate-resources
```

This produces:

```
target/generated-collections/
  My_API_postman.json
  My_API_insomnia.json
  My_API.Production.environment.json
```

## Configuration Reference

| Parameter | Property | Default | Description |
|---|---|---|---|
| `specFile` | `openapi.spec` | `${project.basedir}/src/main/resources/openapi.yaml` | Path to the OpenAPI specification file |
| `outputDirectory` | `openapi.outputDir` | `${project.build.directory}/generated-collections` | Output directory for generated files |
| `formats` | `openapi.formats` | `POSTMAN` | List of formats to generate (`POSTMAN`, `INSOMNIA`) |
| `collectionName` | `openapi.collectionName` | API title from spec | Name used in the output file name |
| `baseUrl` | `openapi.baseUrl` | URL from spec | Base URL override for the collection |
| `fileNamePattern` | `openapi.fileNamePattern` | `{name}_{format}.json` | Output file name pattern. Supports `{name}` and `{format}` placeholders |

### File Name Pattern

The `fileNamePattern` parameter controls the output file name. Available placeholders:

- `{name}` - replaced with the collection name (sanitized)
- `{format}` - replaced with the format in lowercase (`postman`, `insomnia`)

Examples:

```xml
<!-- Default: My_API_postman.json -->
<fileNamePattern>{name}_{format}.json</fileNamePattern>

<!-- Prefix style: postman_My_API.json -->
<fileNamePattern>{format}_{name}.json</fileNamePattern>
```

> **Note:** When generating multiple formats, the pattern **must** contain `{format}` to avoid file name collisions. The plugin will fail with a clear error message if this rule is violated.

### Single Format

To generate only one format, specify a single entry:

```xml
<formats>
    <format>POSTMAN</format>
</formats>
```

When using a single format, the `{format}` placeholder is optional in the file name pattern.

## Requirements

- Java 17+
- Maven 3.9+

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting issues, setting up the development environment, and submitting pull requests.

## Security

If you discover a security vulnerability, please follow the process described in [SECURITY.md](SECURITY.md). Do not open a public issue for security reports.

## Support

[![Donate](https://img.shields.io/badge/Donate-NOWPayments-1A1A1A?logo=bitcoin&logoColor=white)](https://nowpayments.io/donation/rspereiratech)

If this project saves you time, consider supporting development
via [NOWPayments](https://nowpayments.io/donation/rspereiratech).
Every contribution helps keep it maintained — thank you!

## License

[MIT](LICENSE) © 2026 rspereiratech
