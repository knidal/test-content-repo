---
title: Plugins
---

# Plugins

Acme Platform supports a plugin system that lets you extend any service with custom capabilities without forking the codebase. Plugins are small packages that the platform discovers at startup, loads into a sandboxed runtime, and exposes through the public API.

## When to write a plugin

Reach for a plugin when you need behaviour that's specific to your team or environment but doesn't belong in the core platform — domain-specific validators, custom auth flows, integrations with internal tools, or experimental features you want to ship behind a flag.

Anything that needs first-class support across all tenants belongs in core, not in a plugin.

## Plugin shape

A plugin is a Node 20 package with a `plugin.json` manifest and one entry point. The manifest declares the plugin's name, the capabilities it provides, and any permissions it needs. The runtime enforces those declarations.

See [Extra plugin](/plugins/extra-plugin) for a walkthrough of writing your first plugin.
