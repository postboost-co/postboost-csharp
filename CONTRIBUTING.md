# Contributing

Thanks for helping improve PostBoost's open-source tools.

## How this repository is built

SDK repositories (`postboost-python`, `postboost-node`, `postboost-php`, ...) are generated from the PostBoost OpenAPI spec with OpenAPI Generator and published on every release. Generated files are overwritten each time, so:

- **Wrong or missing endpoint, field or type**: open an issue here. We fix it in the spec, and the next release regenerates every SDK.
- **Bug in generated code** (serialization, auth, retries): open an issue with a minimal reproduction. A pull request is welcome as a reference even if we apply the fix in the generator templates instead.
- **Docs and examples**: pull requests welcome.

Hand-written repositories (examples, integrations, the awesome list) accept pull requests directly.

## Running tests locally

Each repository's README lists its build and test commands. Use a test workspace and an API token from **Settings → Access Tokens**; never commit tokens or `.env` files.

## Pull requests

1. Open an issue first for anything larger than a small fix.
2. Keep pull requests focused and describe how you tested them.
3. Sign off your commits (`git commit -s`) to certify the [Developer Certificate of Origin](https://developercertificate.org/).

## Response times

We aim to reply to issues and pull requests within 3 business days.

## Code of conduct

This project follows our [Code of Conduct](CODE_OF_CONDUCT.md).
