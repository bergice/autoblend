---
title: FAQ
---

# Frequently Asked Questions (FAQ)

## How performant is it?
Performance varies depending on factors such as:

* computer specs and resource capacity
* resolution
* shader settings
* how much of the screen is covered by blended seams.

I'll be preparing a demo soon so you can test it out on your own machine.
The goal is to keep render overhead <`1ms` on modern hardware in most scenarios.

Check out the performance and benchmarking details [here](performance.md).

## Which Unreal Engine versions are supported?
Unreal Engine `5.1`-`5.6`. If there's demand I may add `4.x` support as well.

## Which render modes are supported?
Only deferred rendering is supported due to the requirement for a GBuffer channel.
<br/>Static lighting is not supported.

## Why is the Material Ambient Occlusion channel used?
It's the only buffer suitable for custom effects without modifying the engine.
You can work around this by multiplying AO with Base Color instead. 

## Why is there no Discord server, demo, video available? Are you trustworthy?
AutoBlend is a plugin I made for myself for a personal project, and I want to share it with the community.
The first version was developed and released in a week.
I'll be releasing new updates to improve the product as I further develop it.
I'm also planning on releasing a demo so you can try the effect yourself and performance test it on your own hardware before buying.

As for credibility, I am a professional computer programmer with over a decade of experience.
I started using Unreal Engine recently, but am quickly familiarising myself with it as I have a lot of
experience with game development.
You can check out my LinkedIn profile [here](https://www.linkedin.com/in/andreki/).