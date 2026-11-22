# Security

## How updates are protected

Startide downloads updates only from this repository's releases, over HTTPS (TLS with
built-in root certificates, verified against the device's clock). Every file's size and
SHA-256 are listed in the release's manifest, and nothing is installed unless every file
matches. Only the app's own files can be updated; an update can't write outside its folder.

## Reporting a vulnerability

Please **don't open a public issue** for a security problem. Use GitHub's
[private vulnerability reporting](https://github.com/noerdk/startide/security/advisories/new)
instead. You'll get an answer within a week, and a fix in a release as soon as it's ready.

## Supported versions

Only the latest release receives fixes; Startide's updater makes moving to it a single press.
