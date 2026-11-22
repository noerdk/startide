# Third-party notices

The Startide release builds for the Miyoo Mini include the following open-source Rust crates.
Each is used under the licence shown (where a choice is offered, the first is used). Full
licence texts are at the links below and in each crate's source on [crates.io](https://crates.io).

| Crate | Version | Licence |
|---|---|---|
| base64 | 0.22.1 | MIT OR Apache-2.0 |
| block-buffer | 0.10.4 | MIT OR Apache-2.0 |
| cfg-if | 1.0.5 | MIT OR Apache-2.0 |
| crypto-common | 0.1.7 | MIT OR Apache-2.0 |
| digest | 0.10.7 | MIT OR Apache-2.0 |
| displaydoc | 0.2.7 | MIT OR Apache-2.0 |
| form_urlencoded | 1.2.3 | MIT OR Apache-2.0 |
| generic-array | 0.14.7 | MIT |
| getrandom | 0.2.17 | MIT OR Apache-2.0 |
| icu_collections, icu_locale_core, icu_normalizer, icu_normalizer_data, icu_properties, icu_properties_data, icu_provider | 2.4.0 | Unicode-3.0 |
| idna | 1.1.0 | MIT OR Apache-2.0 |
| idna_adapter | 1.2.2 | Apache-2.0 OR MIT |
| libc | 0.2.191 | MIT OR Apache-2.0 |
| litemap | 0.8.3 | Unicode-3.0 |
| log | 0.4.35 | MIT OR Apache-2.0 |
| once_cell | 1.21.4 | MIT OR Apache-2.0 |
| percent-encoding | 2.3.2 | MIT OR Apache-2.0 |
| potential_utf | 0.1.6 | Unicode-3.0 |
| ring | 0.17.14 | Apache-2.0 AND ISC |
| rustls | 0.23.46 | Apache-2.0 OR ISC OR MIT |
| rustls-pki-types | 1.16.0 | MIT OR Apache-2.0 |
| rustls-webpki | 0.103.17 | ISC |
| serde, serde_core | 1.0.229 | MIT OR Apache-2.0 |
| sha2 | 0.10.9 | MIT OR Apache-2.0 |
| smallvec | 1.16.5 | MIT OR Apache-2.0 |
| socket2 | 0.5.10 | MIT OR Apache-2.0 |
| stable_deref_trait | 1.2.1 | MIT OR Apache-2.0 |
| subtle | 2.6.1 | BSD-3-Clause |
| tinystr | 0.8.5 | Unicode-3.0 |
| typenum | 1.20.1 | MIT OR Apache-2.0 |
| untrusted | 0.9.0 | ISC |
| ureq | 2.12.1 | MIT OR Apache-2.0 |
| url | 2.5.9 | MIT OR Apache-2.0 |
| utf8_iter | 1.1.0 | Apache-2.0 OR MIT |
| webpki-roots | 0.26.11, 1.0.12 | CDLA-Permissive-2.0 |
| writeable | 0.6.4 | Unicode-3.0 |
| yoke | 0.8.4 | Unicode-3.0 |
| zerofrom | 0.1.8 | Unicode-3.0 |
| zeroize | 1.9.2 | Apache-2.0 OR MIT |
| zerotrie | 0.2.5 | Unicode-3.0 |
| zerovec | 0.11.9 | Unicode-3.0 |

Build-time only (not in the program): proc-macro2, quote, syn, synstructure, unicode-ident,
serde_derive, yoke-derive, zerofrom-derive, zerovec-derive.

Licence texts: [MIT](https://opensource.org/license/mit) ·
[Apache-2.0](https://www.apache.org/licenses/LICENSE-2.0) ·
[ISC](https://opensource.org/license/isc-license-txt) ·
[BSD-3-Clause](https://opensource.org/license/bsd-3-clause) ·
[Unicode-3.0](https://www.unicode.org/license.txt) ·
[CDLA-Permissive-2.0](https://cdla.dev/permissive-2-0/)

On the device, Startide uses the Miyoo's own system libraries and Onion's `libpadsp` at run
time; they are not part of the release.
