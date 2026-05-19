# Changelog

All notable changes to `parsetoml` will be documented in this file.

## [0.1.1] — 2026-05-19

### Fixed
- Fixed compiler warning: prefixed unused `path` parameter with `_` in `apply_section`.

## [0.1.0] — 2026-05-07

Initial release.

### Added

- `parsetoml.parse` — parse a TOML document string into a `TomlValue`
- `parsetoml.get_string` — read string values from parsed tables
- `parsetoml.get_int` — read integer values from parsed tables
- `parsetoml.get_bool` — read boolean values from parsed tables
- `parsetoml.get_table` — read nested table values
- `parsetoml.get_array` — read array values
- `parsetoml.unwrap_table`, `unwrap_string`, `unwrap_int`, and `unwrap_bool` helpers
- `parsetoml.is_ok`, `is_err`, and `err_msg` helpers
- Support for basic strings, literal strings, integers, booleans, arrays, inline tables, sections, nested sections, and comments
- Self tests covering supported TOML shapes and error cases
