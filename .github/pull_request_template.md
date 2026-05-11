<!--
Thanks for the contribution! Please fill out the sections below.
For larger changes, consider opening an issue first to discuss the approach.
-->

## Summary

<!-- What does this PR do and why? Keep it concise. -->

## Related Issue

<!-- Link the issue this PR addresses, e.g. "Closes #123" or "Refs #45". -->

Closes #

## Type of Change

<!-- Check all that apply. -->

- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing behavior to change)
- [ ] Refactor (no functional change)
- [ ] Dependency version bump (`dependencyManagement`)
- [ ] Property / build configuration change
- [ ] Documentation only

## Area of Change

<!-- Check all that apply. -->

- [ ] `dependencyManagement` (versions, new managed dependency)
- [ ] `properties` (Java / Maven / dependency version properties)
- [ ] Build plugins / lifecycle
- [ ] Project metadata (groupId, version, name, description)
- [ ] Repository files (README, LICENSE, CONTRIBUTING, SECURITY, CODE_OF_CONDUCT, `.github/`)

## Changes

<!-- Bullet list of the main changes. -->

-
-

## Downstream Impact

<!-- This is the parent POM. Changes here can ripple into the child modules (core, postman, insomnia, maven-plugin). Note any expected impact. Delete the section if not applicable. -->

- Affected dependency / property:
- Expected impact on child modules:

## Backwards Compatibility

- [ ] Fully backwards compatible
- [ ] Requires child modules to bump version
- [ ] Breaking change (migration notes below)

<!-- If breaking, describe what consumers / child modules need to do to migrate. -->

## Testing

<!-- How was this verified? -->

- [ ] `mvn clean install` succeeds locally
- [ ] Child modules build successfully against this parent
- [ ] Effective POM verified (`mvn help:effective-pom`)

## Documentation

- [ ] Updated `README.md` (configuration reference, examples)
- [ ] Updated `CONTRIBUTING.md` (if dev workflow changed)
- [ ] Javadoc updated for new/changed public APIs
- [ ] N/A

## Checklist

- [ ] My commits follow the project's commit message conventions
- [ ] I have read [CONTRIBUTING.md](../blob/master/CONTRIBUTING.md)
- [ ] I have read and agree to the [Code of Conduct](../blob/master/CODE_OF_CONDUCT.md)
- [ ] My changes are licensed under the [MIT License](../blob/master/LICENSE)

## Additional Notes

<!-- Anything reviewers should pay special attention to, screenshots, benchmarks, follow-ups, etc. -->
