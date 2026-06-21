---
title: Extra plugin
---

# Extra plugin

This page walks through writing a small plugin end-to-end: scaffolding the package, declaring capabilities, implementing the entry point, and loading the result into a running Acme Platform instance.

## Scaffold

Run `acme plugin init my-plugin` from the directory where you want the plugin to live. The CLI creates a package skeleton with a `plugin.json`, a sample entry point, and a basic test harness.

```bash
acme plugin init my-plugin
cd my-plugin
npm install
```

## Declare what the plugin does

Open `plugin.json` and add the capabilities your plugin exposes. The platform uses this manifest to wire the plugin into the right extension points and to gate any permissions it asks for.

```json
{
  "name": "my-plugin",
  "version": "0.1.0",
  "capabilities": ["validator"],
  "permissions": ["read:configs"]
}
```

## Implement the entry point

The entry point exports a function per declared capability. The runtime calls these functions with a context object that gives the plugin access to anything its permissions allow.

```typescript
export function validator(input, context) {
  // ...
}
```

## Load it

Drop the plugin's directory under `~/.acme/plugins/` and restart the platform, or use `acme plugin install <path>` to load it without a restart. The platform prints a confirmation line per loaded plugin.

For the broader overview, see [Plugins](/plugins/plugins).
