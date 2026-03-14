# dotnet-setup-tools

Install or restore .NET tools with optional caching.

## Inputs

| Input   | Required | Default | Description |
|---------|----------|---------|-------------|
| `tools` | No       | `''`    | One or more .NET tools to install globally, one per line. When omitted, `dotnet tool restore` is used instead. |
| `cache` | No       | `true`  | Cache installed tools to speed up subsequent runs. |

## Usage

### Restore local tools from a manifest

Use this when your repository has a [.NET local tool manifest](https://learn.microsoft.com/dotnet/core/tools/local-tools-how-to-use) (`.config/dotnet-tools.json` or `dotnet-tools.json`).

```yaml
steps:
  - uses: actions/checkout@v4

  - uses: actions/setup-dotnet@v4
    with:
      dotnet-version: '8.x'

  - uses: pl4nty/dotnet-setup-tools@v1
```

### Install tools by name

Use this to install one or more tools globally, specified by name.

```yaml
steps:
  - uses: actions/checkout@v4

  - uses: actions/setup-dotnet@v4
    with:
      dotnet-version: '8.x'

  - uses: pl4nty/dotnet-setup-tools@v1
    with:
      tools: |
        microsoft.cst.attacksurfaceanalyzer.cli
        dotnet-ef
```

