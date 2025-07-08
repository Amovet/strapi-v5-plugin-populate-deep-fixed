# Strapi v5 Plugin Populate Deep (Fixed Fork)

This is a fixed version of the strapi-v5-plugin-populate-deep plugin for Strapi v5.

The plugin allows you to easily and deeply populate related data in your API requests using a simple pLevel parameter, saving you from having to manually write complex populate objects.

## Why this Fork?

This package is a fork of the original strapi-v5-plugin-populate-deep plugin.

The Problem:
The original version of the plugin had a logical bug that caused incorrect and incomplete data loading when working with recursive relations (e.g., when a page collection refers to itself through parent and child fields). At a certain depth level, some relations (like tags) would stop being populated.

The Solution:
The issue was caused by the state for tracking processed models being shared across all branches of the recursion. In this version, the bug is fixed: a copy of the state is now passed to each recursive call. This ensures correct, predictable, and complete data population at any nesting level.

# Installation

`npm install @amovet/strapi-v5-plugin-populate-deep`

`yarn add  @amovet/strapi-v5-plugin-populate-deepp`


# Usages

1. Enabling the Plugin

To activate the plugin, add it to your config/plugins.ts configuration file.
JavaScript

## Examples

1. Populate a request with the default max depth.
   `/api/articles?pLevel`

2. Populate a request with the a custom depth
   `/api/articles?pLevel=10`

## Good to know

- The default maximum depth is 5 levels deep.
- The pLevel parameter works for all collections and single types when using findOne and findMany methods.
- Increasing the depth level may result in longer API response times.

# Configuration

You can configure the default depth globally through the plugin configuration.

## Example configuration

To customize the default depth, add or modify the config/plugins.js file as shown below:
`config/plugins.js`

```
module.exports = ({ env }) => ({
  'strapi-v5-plugin-populate-deep': {
    config: {
      defaultDepth: 3, // Default is 5
    }
  },
});
```

🙏 Credits

This package is a fixed fork. A huge thanks to the original authors and contributors for their foundational work:

    Mustafa ONAL

    Christofer Jungberg

