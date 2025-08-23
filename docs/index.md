---
title: AutoBlend
---

# AutoBlend – Easily blend objects in your scene

## Overview
AutoBlend blends meshes seamlessly into their surroundings using a post process pass and a small material graph change.  
It will automatically compute blend IDs for meshes, but you can override them per material or per object if needed.

Unlike Runtime Virtual Texturing (RVT), Pixel Depth Offset (PDO), and other meshblend techniques, this effect works on any number of meshes at any position - not just where two surfaces meet.

- Flexible placement: Works anywhere in the scene, not only at terrain or surface-level intersections.
- No extra prep: No mesh vertex painting, RVT setup, or additional UVs/vertex data needed.
- Scales well: Adds very little overhead, so it works efficiently even with thousands of meshes.
- No compile-time changes: Drop it into existing materials without rebuilding shaders or the project.

## Setup
1. **Installation**
    - Click the AutoBlend button in the Unreal Editor toolbar to open the plugin window.
    - Install the plugin by clicking the **Install** button.
2. **Add the post process effect**
    - Add a *Post Process Volume* to your level.
    - Add the `M_PostProcess_AutoBlend` material under **Rendering Features → Post Process Materials**.
    - (Optional) Enable **Infinite Extent (Unbound)** to apply the effect everywhere.
3. **Hook up the Blend ID function**
    - Open your mesh base material.
    - Add the `MF_BlendID` material function node.
    - Connect its output appropriately for blending.
    - Repeat for all materials you want to blend.

## Usage
AutoBlend automatically computes a blend ID for every mesh with the material function applied.  
You can override this behavior:

- **Per Material Override**: Set the *Blend ID* scalar parameter in the material instance (affects all meshes using that material).
- **Per Object Override**: Set *Custom Primitive Data [0]* in the mesh instance settings for per-instance control.
