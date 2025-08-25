---
title: Performance
---

# Performance

Performance varies depending on factors such as:

* computer specs and resource capacity
* resolution
* shader settings
* how much of the screen is covered by blended seams.

I'll be preparing a demo soon so you can test it out on your own machine.
The goal is to keep render overhead <`1ms` on modern hardware in most scenarios.

## Time Complexity

Most of the compute time happens in the post process shader which calculates blending per pixel.
Each pixel needs to sample nearby pixels to detect seams.
If a seam is found, blending is calculated.

Cost scales linearly with the number of ray directions and logarithmically with the search radius. The refinement stage adds a small fixed cost.

* **Directions (NumDirs)**: doubles cost if doubled.
* **Radius (MaxRadius)**: increases cost slowly (~`log2(MaxRadius)`).
* **Refinement steps (BinaryRefineIters)**: small linear add.

!!! Example

    (`NumDirs`=`8`, `MaxRadius`=`64`, `BinaryRefineIters`=`4`) yield on the order of ~`80` samples (~`160` texture reads) per pixel in worst-case seam regions; most pixels do less work due to early exit.

## Benchmarks

[//]: # (### MacBook Pro M2 Max)

[//]: # ()
[//]: # (**Specs**:)

[//]: # (MacBookPro M2 Max)

[//]: # (32 GB Memory)

[//]: # (Resolution: )

[//]: # (Unreal Engine Version: 5.6)

[//]: # ()
[//]: # ([//]: # &#40;Quality Settings: High&#41;)
[//]: # ()
[//]: # (#### Forest Scene: `0.5ms`)

[//]: # ()
[//]: # (Radius: 5 / MaxRadius: 20)

[//]: # ()
[//]: # ([//]: # &#40;<div class="grid cards" markdown>&#41;)
[//]: # ()
[//]: # ([//]: # &#40;- **Shader On** ![forest.gif]&#40;media/forest.gif&#41;&#41;)
[//]: # ()
[//]: # ([//]: # &#40;- **Shader On** ![forest.gif]&#40;media/forest.gif&#41;&#41;)
[//]: # ()
[//]: # ([//]: # &#40;- **Shader On GPU Stats** ![forest.gif]&#40;media/forest.gif&#41;&#41;)
[//]: # ()
[//]: # ([//]: # &#40;- **Shader Off GPU Stats** ![forest.gif]&#40;media/forest.gif&#41;&#41;)
[//]: # ()
[//]: # ([//]: # &#40;- **Debug View** ![forest.gif]&#40;media/forest.gif&#41;&#41;)
[//]: # ()
[//]: # ([//]: # &#40;</div>&#41;)
[//]: # ()
[//]: # (=== "Shader On")

[//]: # (    ![forest.gif]&#40;media/forest.gif&#41;)

[//]: # (=== "Shader Off")

[//]: # (    ![desert.gif]&#40;media/desert.gif&#41;)

[//]: # (=== "Shader On GPU Stats")

[//]: # (    ![forest.gif]&#40;media/forest.gif&#41;)

[//]: # (=== "Shader Off GPU Stats" )

[//]: # (    ![forest.gif]&#40;media/forest.gif&#41;)

[//]: # (=== "Debug View" )

[//]: # (    ![forest.gif]&#40;media/forest.gif&#41;)

[//]: # ()
[//]: # ()
[//]: # (TODO: do one with a large radius if it runs well to show that we can increase them)

[//]: # ()
[//]: # ()
[//]: # (### Windows 11)

Coming soon.
