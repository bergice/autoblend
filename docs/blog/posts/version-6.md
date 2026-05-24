---
date:
  created: 2026-05-24
---

# Version 6 is out, Unreal Engine 4.27 support!

AutoBlend now supports Unreal Engine 4.27 in addition to the existing 5.x support.

The install tool also now validates required project settings - **Allow Static Lighting** must be disabled, **Deferred Rendering** must be active, and `r.Lumen.ScreenProbeGather.MaterialAO` must be set to `0`. If any of these are wrong, the tool offers to fix them automatically.

You can get the plugin on the [Unreal Engine Fab marketplace](https://www.fab.com/listings/b474f704-c319-4fd0-87f3-651931da6b33).
