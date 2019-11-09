<style>
img {
	margin: 10px;
}
</style>

# RaindropFX - Pro

FAQ.

## Q: When I use it in the editor in play mode everything works fine. However, when I create a build and start it, the raindrop effect isn't visible anymore. What could be the problem?
### A:  {docsify-ignore}
	1. The problem is mainly caused by the 'Shader.Find' API, custom shaders will not be included into the player build if nothing references it.  
	2. So first you can try to go to 'ProjectSettings->Graphics' in your Unity editor then add all the 5 shaders of RaindropFX (located at : RaindropFXPro/Shaders/HDRP) to 'always included shaders', then rebuild your game and try it again.  
	3. If you try to build an apk for Android platform, you can try to do the following:  
		- File -> Build Settings  
		- Click "Player Settings"  
		- Navigate to the Android tab  
		- Unfold the "Other Settings" menu  
		- Uncheck "Auto Graphics API"  
		- Remove OpenGLES2 and Vulkan graphics API's  
		- Set the Minimum API Level to be greater than Android 4.3.

<div align=center><img width="80%" src="_pics/RFXP_150/problem_01.png"/></div>
<div align=center><img width="80%" src="_pics/RFXP_150/problem_02.png"/></div>
	

## Q: How is the Lite version different from the Pro version?
### A:  {docsify-ignore}
		RaindropFX PRO is integrated with Unity's Post Processing Stack (V2), so you can use RaindropFX PRO with same features in everywhere you can use Post Processing Stack (V2).  
		Lite version (RaindropFX 0.5.0) does not support SRP (HDRP/LWRP/custom), it only support Deferred and Forward rendering and has fewer features (screen fog, wind turbulence ...), but it can work without Unity's Post Processing Stack (V2), and can work with older versions (5.3.4 or higher) Unity.

## Q: Does it support waterdrops without a physics/fall/wind effect, so only the drops?
### A:  {docsify-ignore}
	There are two ways to achieve the desired results:  
		1. Set the magnitude of gravity and wind to 0.
		2. Drops are divided into two types: static and dynamic. You can set the maximum number of these two kinds of droplets separately, so you can just set the number of dynamic droplets to 0, so that only static droplets can be generated in random positions on the screen.

## Q: Is it possible to use RaindropFX Pro on a glass material to use it on windows etc.?
### A: {docsify-ignore}
	Preview version of object space version RaindropFX has been released and included in version 1.50  
	you can find a preview video of the final version at forum:   

https://forum.unity.com/threads/raindropfx-realistic-camera-lens-rain-effect.519068/#post-3402707

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.