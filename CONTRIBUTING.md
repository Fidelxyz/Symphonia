# Contribution Guidelines

Thank you for your interest in contributing to Symphonia!

There are many ways you may contribute. Some ideas for possible contributions are provided below.

## Ways to Contribute

### Implement new format readers, decoders, and features

Implement missing features from the project roadmap, or features that haven't been considered yet.

### Triage and fix reported issues

Reproduce, root cause, and submit bug fixes for reported issues.

### Benchmark and optimize

Benchmark, identify, and report areas where performance could be improved. If possible, try your hand at optimizing it yourself!

### Improve documentation

Identify areas of the documentation that are lacking and expand them. Adding examples is another great way to help document the project for new users.

### Test your content library

Test your content library against Symphonia and ensure there are no panics or audio glitches.

The [`symphonia-play`](symphonia-play/README.md) and [`symphonia-check`](symphonia-check/README.md) utilities may be used for this, but please note the section about interpreting results of the latter since false positives are not uncommon.

### Answer questions

Answer questions raised in issues or discussions.

## Code & Documentation Contribution Guidelines

Please read through these guidelines ahead of time to ensure a smooth contribution process.

### General Considerations

Symphonia is a mature project with a limited number of maintainers. Therefore, maintainability and preventing regressions are very important considerations when we accept contributions.

We welcome pull requests (PRs) for new format readers, decoders, and other missing features. It is a good idea to raise an issue ahead of time to let everyone know what you will be working on to reduce the chance of duplicate efforts, and to make sure the change is aligned with the project. Once merged, please also consider  volunteering to take responsibility for the on-going maintenance of the new code.

While PRs containing isolated changes can usually be merged and included in the next release, PRs with the following changes may be delayed for some time:

- SemVer or API breaking changes. Please read what constitutes a SemVer break in the Cargo [book](https://doc.rust-lang.org/cargo/reference/semver.html).
- Directly or indirectly increasing the minimum supported Rust version (MSRV). We consider this a SemVer breaking change.

In general, we won't accept PRs for the following changes without prior discussion and approval:

- Wholesale rewrites of a crate or feature.
- Replacing most, or all, of a crate or feature's implementation with an out-of-tree dependency.
- Changing an API or modifying the behaviour of Symphonia to specifically match the requirements of one project or application.

### Quality

Symphonia reads untrusted data which may be corrupted or deliberately malicious. It is critical that Symphonia validates and sanity-checks all data. Under no circumstance should Symphonia panic or consume an unbounded amount of system resources (e.g., RAM).

A baseline level of quality is required before a PR is merged. All known audio glitches should be fixed, and the potential harm of any undiscovered audio glitch should be minimized.

The build must be free of any warnings.

Running clippy against the change is recommended, but not mandatory. Fuzzing is also recommended, but not mandatory.

### Code Formatting

Please format your code prior to submission with a **nightly** build of `rustfmt`. After installing the nightly toolchain you can do this by running `cargo +nightly fmt`.

GitHub will not allow a PR to be merged that does not meet the code formatting standard.

### Testing

Adding unit tests for your code is recommended, but not mandatory.

Please run `cargo test` before submission.

GitHub will not allow a PR to be merged that has failing test cases.

### Documentation

If your change modifies the behaviour of a public
API, please also update the relevant documentation. This may also include [`GETTING_STARTED.md`](GETTING_STARTED.md) and any examples.

If you reference any standards, please make note of it in the comments of your implementation. For example, if your code includes a lookup table of constants, add a comment indicating the standard and the section from which it came from.

### Acknowledgements

If you are a new contributor, please add yourself to the [`CONTRIBUTORS`](CONTRIBUTORS) file.

If you are introducing a new crate, add yourself as the **first** author of the crate.

### Commit History

Unless otherwise requested, all PRs will be squashed into a single commit to maintain a clean history. If you would prefer that the commit history is kept, please ensure that it is clean. All commits should be meaningful and have a title that follows the general `component: Description of change.` style.

### License

Please be aware that all contributions must be licensed under the MPL v2.0 license.
