## Google Summer of Code 2017 - final report
## Volume Rendering for appleseed

As a participant of Google Summer of Code I was working on volume rendering for [appleseed]('http://appleseedhq.net).
You can find the proposal of my project at the following link: [original proposal](https://github.com/Biart95/appleseed-volumetric-rendering-proposal/blob/master/proposal.md).
During the summer I successfully reached most of the proposed goals, allowing the appleseed to create its first volume renders.
Below you can find the detailed results of my work.

### Community bonding period

In the beginning of my GSoC I was discussing the future project with my mentors. We defined the scope of our project that
appeared to be pretty big and decided that we should concentrate on rendering part and leave OSL volume shaders for the
after-GSoC work. On the other hand, we found a couple of publications that can significantly improve the quality of volume 
rendering ([1], [2]) and decided to include them in the summer schedule.

Most importantly, during the spring I examined almost the whole rendering core of appleseed and got familiar with 
friendly and helping appleseed community. I also fixed a few minor bugs ([#1351](https://github.com/appleseedhq/appleseed/pull/1351),
[#1352](https://github.com/appleseedhq/appleseed/pull/1352)), implemented IES parser
([#1414](https://github.com/appleseedhq/appleseed/pull/1414)) and made first steps in developing IES lights project
(more details [here](https://github.com/appleseedhq/appleseed/wiki/List-of-Project-Ideas-for-GSoC-2017#project-2-ies-light-profiles)).

### Coding period and results

Here is the list of deliverables that were successfully achieved:

- Raymarching engine that extends appleseed path tracer and is capable of rendering homogeneous participating media inside
closed surfaces
- Support for both single and multiple scattering
- Support for advanced distance sampling for volume rendering based on the [1]
- Complex multiple importance sampling for distance sampling and light sampling based on the [1] and [2]
- Database consisting of reference images that are used to compare and test rendering results
- New _Volume_ entity exposed to the UI of appleseed.studio

There is also a [Volume Rendering project page]() where we keep track on tasks related to volume rendering and this 
GSoC project in particular.

### Source code

Source code consists of a few pull requests, most of which were merged and became a part of appleseed software.

List of merged pull requests:

- [Volume Rendering - Entities](https://github.com/appleseedhq/appleseed/pull/1434)
- [Raymarcher that can compute absorption](https://github.com/appleseedhq/appleseed/pull/1446)
- [Volume Rendering - Simple Scattering](https://github.com/appleseedhq/appleseed/pull/1465)
- [Fixes of path tracer and lighting engines](https://github.com/appleseedhq/appleseed/pull/1492)
- [Small tweaks](https://github.com/appleseedhq/appleseed/pull/1503)
- [Implement clever per-channel distance sampling for participating media](https://github.com/appleseedhq/appleseed/pull/1518)
- [Get rid of templates in Tracer and fix bug in distance sampling](https://github.com/appleseedhq/appleseed/pull/1531)
- [Fix critical bug in volume distance sampling](https://github.com/appleseedhq/appleseed/pull/1538)
- [Volumetric entities redesign](https://github.com/appleseedhq/appleseed/pull/1545)
- [Basic multiple scattering](https://github.com/appleseedhq/appleseed/pull/1556)
- [Fix most of the warnings in appleseed GCC 7 build](https://github.com/appleseedhq/appleseed/pull/1577)

Pull requests waiting for approval:

- [Better importance sampling for volumes](https://github.com/appleseedhq/appleseed/pull/1591)

### Example renders

Lanterns demonstrating advanced importance sampling with single scattering, rendered at 64 sample/pixel:
![Lanterns, 64 samples/pixel](lanterns%20-%20equiangular%20sampling%20-%2064s.png)

Cloud shaped as stanford bunny, multiple scattering, 128 sample/pixel:
![Bunny cloud, 128 samples/pixel, diffuse EDF](bunny%20-%20128s%20-%20isotropic.png)

The similar bunny with less dense media, lighted using cone EDF, 128 sample/pixel:
![Bunny cloud, 128 samples/pixel, cone EDF](bunny%20-%20128s%20-%20cone.png)

### References

1. 
2. 
