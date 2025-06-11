# lizard-pre-commit

A [pre-commit](https://pre-commit.com/) hook for [Lizard](https://github.com/terryyin/lizard), a code complexity analyzer that supports multiple programming languages.

## Using Lizard with pre-commit

To run Lizard's code complexity analysis via pre-commit, add the following to your `.pre-commit-config.yaml`:

```yaml
repos:
  - repo: https://github.com/Guilherme-Jorge/lizard-pre-commit
    # Lizard version
    rev: v0.0.1
    hooks:
      - id: lizard
```

## Supported Languages

Lizard supports a wide range of programming languages:

- C/C++ (works with C++14)
- Java
- C# (C Sharp)
- JavaScript (With ES6 and JSX)
- TypeScript (With TSX)
- VueJS
- Objective-C
- Swift
- Python
- Ruby
- TTCN-3
- PHP
- Scala
- GDScript
- Golang
- Lua
- Rust
- Fortran
- Kotlin
- Solidity
- Erlang
- Zig
- Perl

This pre-commit hook does not support:

- TTCN-3
- Fortran
- Erlang

## Configuration Options

Lizard provides a comprehensive set of command-line options to customize its behavior:

### Basic Options
- `-h, --help`: Show help message and exit
- `--version`: Show program's version number and exit
- `-V, --verbose`: Output in verbose mode (long function name)
- `-w, --warnings_only`: Show warnings only, using clang/gcc's warning format
- `--warning-msvs`: Show warnings only, using Visual Studio's warning format

### Language and File Options
- `-l LANGUAGES, --languages LANGUAGES`: List of programming languages to analyze (e.g., `-l cpp -l java`)
- `-f INPUT_FILE, --input_file INPUT_FILE`: Get a list of filenames from the given file
- `-o OUTPUT_FILE, --output_file OUTPUT_FILE`: Output file (format inferred from extension)
- `-x EXCLUDE, --exclude EXCLUDE`: Exclude files matching the pattern (e.g., `"./folder/*"`)
- `-E EXTENSIONS, --extension EXTENSIONS`: Use extensions:
  - `-Ecpre`: Ignore code in the #else branch
  - `-Ewordcount`: Count word frequencies and generate tag cloud
  - `-Eoutside`: Include global code as one function
  - `-EIgnoreAssert`: Ignore all code in assert
  - `-ENS`: Count nested control structures

### Thresholds and Limits
- `-C CCN, --CCN CCN`: Threshold for cyclomatic complexity number (default: 15)
- `-L LENGTH, --length LENGTH`: Threshold for maximum function length (default: 1000)
- `-a ARGUMENTS, --arguments ARGUMENTS`: Limit for number of parameters
- `-i NUMBER, --ignore_warnings NUMBER`: Exit normally if warnings ≤ NUMBER
- `-T THRESHOLDS, --Threshold THRESHOLDS`: Set limit for a field (nloc, cyclomatic_complexity, etc.)

### Output Format Options
- `-X, --xml`: Generate XML in cppncss style
- `--csv`: Generate CSV output
- `-H, --html`: Output HTML report
- `--checkstyle`: Generate Checkstyle XML output

### Performance and Analysis Options
- `-t WORKING_THREADS, --working_threads WORKING_THREADS`: Number of working threads (default: 1)
- `-m, --modified`: Calculate modified cyclomatic complexity number
- `-s SORTING, --sort SORTING`: Sort warnings by field (nloc, cyclomatic_complexity, etc.)
- `-W WHITELIST, --whitelist WHITELIST`: Path to whitelist file (default: './whitelizard.txt')

### Example Configurations

Basic usage with warnings only:
```yaml
repos:
  - repo: https://github.com/your-username/lizard-pre-commit
    rev: v0.0.1
    hooks:
      - id: lizard
        args: ["--warnings_only"]
```

Advanced usage with custom thresholds and exclusions:
```yaml
repos:
  - repo: https://github.com/your-username/lizard-pre-commit
    rev: v0.0.1
    hooks:
      - id: lizard
        args: [
          "--CCN", "10",
          "--length", "800",
          "--arguments", "5",
          "--exclude", "*/tests/*",
          "--working_threads", "4"
        ]
```

## License

lizard-pre-commit is licensed under either of

- Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in lizard-pre-commit by you, as defined in the Apache-2.0 license, shall be dually licensed as above, without any additional terms or conditions.
