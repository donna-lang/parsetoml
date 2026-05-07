# parsetoml

<img src="https://img.shields.io/badge/Donna-parsetoml-FF6347?style=for-the-badge" alt="Donna parsetoml"/>

<a href="https://donna-lang.github.io/parsetoml/">
  <img src="https://img.shields.io/badge/Docs-Read-2F81F7?style=for-the-badge" alt="Docs - Read"/>
</a>

TOML parsing for the [Donna](https://github.com/donna-lang/donna) programming language.

## Overview

`parsetoml` parses a practical subset of TOML into Donna values.

It supports strings, integers, booleans, arrays, inline tables, sections, nested sections, line comments, and inline comments.

## Installation

Add to your `donna.toml` as a dependency:

```toml
[dependencies]
parsetoml = { git = "https://github.com/donna-lang/parsetoml", version = ">=0.1.0 and <1.0.0" }
```

Then import the module:

```donna
import parsetoml
```

## Quick start

```donna
import parsetoml

pub fn parse_config() -> String:
  let src = "name = \"site\"\n[build]\noutput = \"public\""
  let toml = parsetoml.unwrap_table(parsetoml.parse(src))
  parsetoml.get_string(toml, "name")
  |> parsetoml.unwrap_string
```

Read nested tables:

```donna
import parsetoml

pub fn build_output() -> String:
  let src = "[build]\noutput = \"public\""
  let toml = parsetoml.unwrap_table(parsetoml.parse(src))
  case parsetoml.get_table(toml, "build"):
    parsetoml.Err(_) -> ""
    parsetoml.Ok(build) ->
      parsetoml.get_string(build, "output") |> parsetoml.unwrap_string
```

Run tests:

```sh
donna test
```

## API

For API Reference visit the generated docs [here](https://donna-lang.github.io/parsetoml/)

## Supported TOML

```toml
name = "value"
path = '../lib'
count = 42
enabled = true
items = ["a", "b"]
pkg = { path = "../lib", version = "0.1.0" }

[build]
output = "public"

[site.menu]
weight = 10
```

Not supported yet: floats, dates, multi-line strings, and array-of-tables.

## Licence

MIT
