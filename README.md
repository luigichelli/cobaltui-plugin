# pluginMAUI for Cobalt UI

## Description

`pluginMAUI` is a Cobalt UI plugin designed to generate XAML `ResourceDictionary` files from design tokens. This plugin simplifies theme creation for projects using Microsoft's MAUI framework by allowing selective theming with mode-specific overrides.

## Features

- **Selective Token Exclusion:** Exclude tokens by collection name using regular expressions.
- **Mode-specific Overrides:** Generates a base `theme.xaml` with default values and additional files for each token collection with more than a single mode.
- **Supported Token Types:** Color, dimension, typography, and shadow tokens.

## Installation

### Manual Installation

To manually install `pluginMAUI`, follow these steps:

1. Download the latest version of `pluginMAUI` from this GitHub repository
2. Move the pluginMAUI.js to the `plugins` directory at the root of your project.

## Usage

To use `pluginMAUI`, import it into your Cobalt UI configuration. If needed, set up the exclude pattern to omit tokens.

Example configuration to exclude tokens starting with "colorbase":

```javascript
import pluginMAUI from "./plugins/pluginMAUI.js";

export default {
  plugins: [
    pluginMAUI({
      excludePatterns: ["^colorbase"]
    }),
  ],
};
```

## Detailed Functionality

`pluginMAUI` generates a base `theme.xaml` file containing all tokens at their default values. For collections with tokens that support multiple modes, it generates additional XAML files allowing for mode-specific overrides.

### Shadow Tokens

Handling shadow tokens requires special consideration as MAUI does not support multiple shadows by default. If a token has more than one shadow, an index is appended to the token name to differentiate them. For example:

```xml
<Shadow x:Key="Effects.shadow-100-1" Color="#0000000a" Radius="4" Opacity="1" OffsetX="0" OffsetY="1"/>
<Shadow x:Key="Effects.shadow-100-2" Color="#ffffff33" Radius="0.25" Opacity="1" OffsetX="0" OffsetY="-0.5"/>

<Shadow x:Key="Effects.shadow-200-1" Color="#0000000d" Radius="8" Opacity="1" OffsetX="0" OffsetY="3"/>
<Shadow x:Key="Effects.shadow-200-2" Color="#ffffff33" Radius="0.25" Opacity="1" OffsetX="0" OffsetY="-0.5"/>
```

In your application, these indexed shadows should be handled appropriately to achieve the desired visual effects.

## Contributing

Contributions are welcome!

## License

`pluginMAUI` is made available under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Acknowledgments

Thanks to the Cobalt UI team for their robust plugin development framework, which facilitated the creation of `pluginMAUI`.
