# RaindropFX - Changes

Revision History.

## [URP] Version 1.8.0
### Added {docsify-ignore}
	- Support for Unity 6/URP 17.0+ added
	- Simplify the process of configuring Render Features

### Fixed {docsify-ignore}
	- GPU solver with uneven raindrop density
	- Several shader warnings
	- The downsampling parameter of the screen space version solver are not taking effect correctly
	- Optimize the cutout effect of GPU raindrops

## [HDRP] Version 3.5.0
### Added {docsify-ignore}
	- Support for Unity 6/HDRP 17.0.3+ added
	- Add parameter classification to the object surface raindrop solver component panel

### Fixed {docsify-ignore}
	- GPU solver with uneven raindrop density
	- Several shader warnings
	- The downsampling parameter of the screen space version solver are not taking effect correctly

## [URP] Version 1.5.1
### Added {docsify-ignore}
	- Support for URP 14.0+ added
	- Screen space GPU solver
	- Kawas blur is implemented to replace Gaussian blur (you can get 4 times performance increasement without lose quality)

### Fixed {docsify-ignore}
	- 'hasAdvancedMode' error in Unity 2021+
	- Parameter range limit is broken

## [HDRP] Version 3.2.0
### Added {docsify-ignore}
	- improved raindrop visual quality (GPU solver)
	- dynamic wipe for GPU solver
	- raindrop size control for GPU solver
	- lifetime control for GPU solver

### Fixed {docsify-ignore}
	- GPU solver generate non-uniform distribution raindrops
	- error while using new input system
	- 'hasAdvancedMode' error in Unity 2021+

### Removed {docsify-ignore}
	- mouse paint function is deprecated

## [URP] Version 1.0.0
### First Release {docsify-ignore}
	- All basic functions EXCEPT GPU solver

## [STD] Version 2.5.3
### Added {docsify-ignore}
	- assembly definition added

### Fixed {docsify-ignore}
	- Non-uniform raindrop distribution while using GPU solver
	- broken example scene is recreated
	- namespace changed to 'STD'

## [HDRP] Version 3.0.0
### Fixed {docsify-ignore}
	- shader error in HDRP 10.2.2

### Added {docsify-ignore}
	- half batches decreased (CPU solver)
	- dynamic wipe for object space version (CPU solver)
	- raindrop painting (screen space, CPU solver)
	- force LUT (affecting the flow direction of water droplets on object surface)
	- assembly definition
	- dynamic scaling of full screen raindrop texture (no longer need to preset the size at the beginning of the game)
	- controllable fogging speed
	- GPU screen space solver (beta)
	- GPU object space solver (beta)
	- fluids can interact with normal map (object space, GPU solver)

## [STD/HDRP] Version 2.5.0
### Added {docsify-ignore}
	- dynamic wipe effect
	- droplet pixelization for pixel style games
	- screen rain mask

## [STD/HDRP] Version 2.0.0
### Added {docsify-ignore}
	- Radial wind
	- Tint color for droplets
	- Accurate foreground droplet blur
	- Stable object space version
	- Better visual quality of object space version
	- Batches reduced by 5 from the previous version when there are no droplets in scene

### Fixed {docsify-ignore}
	- Error with null raindrop texture
	- FPS dropping down even when there are no drops on screen
	- Enabling HDR option of camera causes an error in object space version
	- object space version is now compatible with AURA2

## [STD] Version 1.5.0
### Added {docsify-ignore}
	- Solver core is completely refactored
	- Object space raindrop solver (Non-physical Accuracy) [Preview]
	- Batch image renderer added (Apply raindrop effect to a set of custom pictures)

### Fixed {docsify-ignore}
	- More accurate screen distortion result based on calculated normal map
	- A crash problem caused by running multiple solvers simultaneously

## [STD] Version 1.0.1
### Added {docsify-ignore}
	- Wind turbulence
	- Foreground water droplets blur
	- Screen fog
	- Bonus post stacks
	- More adjustable parameters
	- Support for SRP (Scriptable Render Pipeline)

### Fixed {docsify-ignore}
	- Wrong visual effect when screen scale is not 16:9
	- Drawcall reduced
	
## [STD/Lite] Version 0.6.0
### Added {docsify-ignore}
	- Tint color
	- Wind

## [STD/Lite] Version 0.5.0
### First Release {docsify-ignore}
	- Base functions implemented

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.