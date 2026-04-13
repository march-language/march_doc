# march_doc

HTML documentation generator for [March](https://github.com/march-language/march) projects.

## Usage

Install as a forge archive:

```sh
forge install march_doc
```

Then from any March project with a `lib/` directory:

```sh
forge march_doc.doc
```

This reads the package name from `forge.toml`, parses all `.march` files in `lib/`, and generates static HTML docs to `docs/{package_name}/`.

## Features

- **Module pages** — one page per module with functions, types, and interfaces
- **Doc strings** — renders `doc "..."` and `doc """..."""` annotations as formatted HTML with Markdown support (headings, code blocks, inline code, bold, italic, links)
- **Cross-module search** — fuzzy search across all modules, functions, types, and signatures via a generated `search-index.json`
  - Levenshtein distance for typo tolerance
  - Substring and word-boundary matching (camelCase, snake_case)
  - Weighted scoring: name > signature > module > doc
- **Dark theme** with syntax-highlighted badges for `fn`, `pfn`, `type`, `ptype`, and `interface`
- **Collapsible items** — click any function/type to expand its documentation
- **Copy buttons** on code blocks

## Project structure

```
lib/
  march_doc.march              orchestrator (generate)
  march_doc/
    parser.march               extract modules, fns, types, ifaces from source
    html.march                 render HTML pages with CSS/JS
    markdown.march             Markdown → HTML conversion
    discovery.march            recursive .march file discovery
    search_index.march         build JSON search index
forge/
  doc.march                    forge task entry point
test/
  test_parser.march            parser tests
  test_html.march              HTML rendering tests
  test_markdown.march          Markdown conversion tests
  test_discovery.march         file discovery tests
  test_integration.march       end-to-end generation tests
```

## Development

Requires the [March](https://github.com/march-language/march) compiler and `forge` in your PATH.

```sh
# Run tests
forge test

# Run tests with coverage
forge test --coverage

# Generate docs for this project
forge march_doc.doc
```

## License

MIT
