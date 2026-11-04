# Changelog

All notable changes to this project are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- `ApiKeysConfig`, passed to `init`, which holds the Bintable API key. The client sends it as the `api_key` query parameter on every request.
- An optional `headers` parameter on every remote method, for sending extra request headers.
- Documentation for the fields of `ResponseItem`.
- New `ConnectionConfig` fields, taken from `http:ClientConfiguration`: `followRedirects`, `cookieConfig`, `socketConfig` and `laxDataBinding`.

### Changed

- **Breaking:** `init` takes a required `ApiKeysConfig` as its first parameter. In 1.5.2 it took no credentials, and each method took the API key instead.
- **Breaking:** the remote methods are renamed and no longer take the API key:
  - `binLookup(string bin, string apiKey)` is now `lookupBin(string bin)`.
  - `balanceLookup(string apiKey)` is now `getBalance()`.
- **Breaking:** `ConnectionConfig.http1Settings` is now `http:ClientHttp1Settings` (was the connector's own `ClientHttp1Settings`).
- `ConnectionConfig.timeout` defaults to 30 seconds (was 60).

### Removed

- **Breaking:** the connector's own `ClientHttp1Settings` and `ProxyConfig` records. Use `http:ClientHttp1Settings` and `http:ProxyConfig` instead.
