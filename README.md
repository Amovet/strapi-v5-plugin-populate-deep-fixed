#Strapi v5 Plugin Populate Deep (Fixed Fork)

This is a fixed version of the strapi-v5-plugin-populate-deep plugin for Strapi v5.

The plugin allows you to easily and deeply populate related data in your API requests using a simple pLevel parameter, saving you from having to manually write complex populate objects.

🛠️ hat Was Fixed?

This package is a fork of the original strapi-v5-plugin-populate-deep plugin.

The Problem:
The original version of the plugin had a logical bug that caused incorrect and incomplete data loading when working with recursive relations (e.g., when a page collection refers to itself through parent and child fields). At a certain depth level, some relations (like tags) would stop being populated.

The Solution:
The issue was caused by the state for tracking processed models being shared across all branches of the recursion. In this version, the bug is fixed: a copy of the state is now passed to each recursive call. This ensures correct, predictable, and complete data population at any nesting level.

⚙️ Installation

Bash


    npm install @amovet/strapi-v5-plugin-populate-deep



🚀 Usage

1. Enabling the Plugin

To activate the plugin, add it to your config/plugins.js configuration file.
JavaScript



    ./config/plugins.js
    
    module.exports = ({ env }) => ({  
      '@amovet/strapi-v5-plugin-populate-deep': {
        enabled: true,
        },
    });
    


2. Usage in API Requests

Simply add the pLevel=<depth> parameter to any GET request for a collection or a single entry.

Example:

To get articles entries with all related data populated up to 3 levels deep, use the following request:

    GET /api/articles?pLevel=3


This will automatically populate all relations, components, and dynamic zones up to the specified level.

🙏 Credits

This package is a fixed fork. A huge thanks to the original authors and contributors for their foundational work:

    Mustafa ONAL

    Christofer Jungberg
