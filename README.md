# Syntax Configurations

A collection of syntax configuration files for [ped](https://github.com/davidledwards/ped).

## Installing

The easiest method of installation is to clone this repository into a directory where `ped` will automatically discover and load configuration files.

For example, the following will clone this repository into a directory known to `ped`.

```shell
mkdir ~/.ped
git clone https://github.com/davidledwards/ped-syntax.git ~/.ped/syntax
```

Updating syntax configurations is as simple as pulling the latest commit.

```shell
cd ~/.ped/syntax
git pull
```

## Configurations

Syntax configuration files are formatted according to the [TOML](https://toml.io) specification.

The following example illustrates the expected layout. Under `[syntax]`, `name` is a canonical name given to the syntax definition and `extensions` is an array of one or more file extensions without the preceding dot.

The `[tokens]` table contains any number of regular expressions as keys and 2-tuples as values representing colors, where the first number is the foreground and the second is the background, both in the range of `0` to `255`. The order of tokens is important because earlier patterns will match before later patterns.

```toml
[syntax]
name = "C"
extensions = ["c", "h"]

[tokens]
# Numbers
'[+-]?\d+(\.\d+)?([eE][+-]?\d+)?' = [4, 232]

# Comments
'//.*$' = [8, 232]
'/\*[\s\S]*?\*/' = [8, 232]
```

The `ped` editor uses the [regex-lite](https://docs.rs/regex-lite/latest/regex_lite/index.html) library for compiling patterns defined under `[tokens]`. As a consequence, token patterns must conform to the requirements and limitations defined by this library.

## Contributing

Please refer to the [contribution guidelines](CONTRIBUTING.md) when reporting bugs and suggesting improvements.

## License

Copyright 2024 David Edwards

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
