# D2 CLI

## Install

```bash
curl -fsSL https://d2lang.com/install.sh | sh -s -- --dry-run


# First, install D2
# curl -fsSL https://d2lang.com/install.sh | sh -s --
# echo 'x -> y -> z' > in.d2
# d2 --watch in.d2 out.svg


curl -fsSL https://d2lang.com/install.sh | sh -s -- && d2 layout install elk
```

## Test

```d2
# 声明使用 elk 布局
direction: right
vars: {
  d2-config: {
    layout-engine: elk
  }
}

集控柜: {
  PLC: {
    CPU模块
    通信模块 -> 龙芯芯片
  }
  电源模块 -> PLC.CPU模块
}

传感器阵列 -> 集控柜.PLC: 4-20mA信号
```

```bash
d2 test.d2 test.svg
```

## CLI Usage

### Basic Commands

- **Render a diagram**:
  ```bash
  # Render to SVG (default)
  d2 input.d2 output.svg

  # Render to other formats (png, pdf, pptx, gif, txt)
  d2 input.d2 output.png
  d2 input.d2 output.pdf

  # Read from stdin, write to stdout
  cat input.d2 | d2 - - > output.svg
  ```

- **Live Preview / Watch mode**:
  ```bash
  d2 --watch input.d2 output.svg
  # or using the short flag
  d2 -w input.d2 output.svg
  ```

- **Format code**:
  ```bash
  d2 fmt input.d2
  ```

- **Validate syntax**:
  ```bash
  d2 validate input.d2
  ```

- **Open in online playground**:
  ```bash
  d2 play input.d2
  ```

- **List layouts / themes**:
  ```bash
  # List all available layout engines
  d2 layout

  # Show detailed help and flags for a specific layout engine
  d2 layout elk

  # List all available themes
  d2 themes
  ```

### Common Flags

| Flag | Env Variable | Description | Default |
| :--- | :--- | :--- | :--- |
| `-l, --layout <name>` | `$D2_LAYOUT` | Layout engine to use (`dagre`, `elk`, etc.) | `dagre` |
| `-t, --theme <id>` | `$D2_THEME` | Theme ID to use (e.g., `0` for Neutral Default, `100` for Vanilla Nitro Cola) | `0` |
| `--dark-theme <id>` | `$D2_DARK_THEME` | Theme ID to use in dark mode | `-1` (follows `--theme`) |
| `-s, --sketch` | `$D2_SKETCH` | Render with a hand-drawn sketch style | `false` |
| `--scale <float>` | `$SCALE` | Scale output size (e.g., `0.5` to half size) | `-1` |
| `--pad <int>` | `$D2_PAD` | Padding in pixels around the rendered diagram | `100` |
| `--no-xml-tag` | `$D2_NO_XML_TAG` | Omit `<?xml ...?>` declaration from SVG for inline HTML use | `false` |

## Uninstall

```bash
curl -fsSL https://d2lang.com/install.sh | sh -s -- --uninstall
```
