# RaindropFX Pro URP (1.00)

Easy to use realistic camera lens raindrop animation effects for URP 10.3.1+.

## 1 Getting started
### 1-1 Download RaindropFX to your project
!> **Important** If you have any old version RaindropFX, delete it first.

1. Please make sure your project is using high-definition rendering pipeline;
2. If you have any old version RaindropFX, delete it;
3. Then download and import new version RaindropFX URP package to your project.

### 1-1 Post processing stack setup
Find ‘Forward Renderer Data’ asset of your rendering pipeline, then add ‘RFX Blur Pass’ and ‘Raindrop FX_URP Render Feature’ to ‘Renderer Features’:

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (1).png"/></div>
<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (2).png"/></div>

## 2 Raindrop solver
### 2-1 Screen space version
#### Volume setup {docsify-ignore}
Select any object in your scene, and add a ‘Volume’ component.

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (3).png"/></div>

#### Raindrop effect setup {docsify-ignore}
On the ‘Volume’ component, choose a profile in the profile field or create a new profile, then click ‘Add Override’, go to ‘Post-processing -> RaindropFX -> RaindropFX_URP’ to add the raindrop effect.

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (4).png"/></div>

Raindrop texture must be set before you can use RaindropFX. Find the raindrop texture at ‘RaindropFX_URP/Resources/Textures/raindrop_a’. Or you can use your own raindrop texture.

<div align=center><img width="90%" src="_pics/RFXU_100/RFXU100_PIC_ (5).png"/></div>

Now you can see the raindrop effect in your scene.

<div align=center><img width="90%" src="_pics/RFXHD_200/hd (6).png"/></div>

#### Setup wipe effect {docsify-ignore}

If you want to enable wipe effect, first add ‘Wiper’ component to your main camera;

<div align=center><img width="60%" src="_pics/RFXHD_300/2.png"/></div>

Add your ‘Volume’ component to ‘Post Volumn’, then add all the wipers to ‘Wipers’ (you can set the size of the ‘Wipers’ to any number you like. For example, if you want to use two wipers, set it to 2, then drag and drop your wipers into the slots);

<div align=center><img width="90%" src="_pics/RFXU_100/RFXU100_PIC_ (9).png"/></div>

All wipers must be placed in a specific layer. You can directly enter a layer number that has never been used in the scene to the ‘Cull Layer’ slot, and then the script will automatically move all the wipers to this layer at the beginning of the game without manual setting;

!>The script don't handle child objects. If your wiper contains child objects, please set layer of them manually.

!>If you want to hide the wipers in the game view, just exclude the cull layer in your main camera.

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (10).png"/></div>

Assign ‘Wiper’ material (located at: RaindropFX_URP/Resources/Materials) to all of your wipers. Or you can use your own material. The color of wiper from black to white represents different wipe power, and white represents complete wipe;

<div align=center><img width="90%" src="_pics/RFXU_100/RFXU100_PIC_ (11).png"/></div>

Then tick the ‘Wipe Effect’ in the ‘Raindrop FX_URP’ in the ‘Volume’ component;

<div align=center><img width="70%" src="_pics/RFXHD_300/4.png"/></div>

Finally, run your game and drag your wiper, you’ll see the wipe effect. The wipe effect affects both water droplets and the screen fog.

<div align=center><img width="70%" src="_pics/RFXHD_300/4-2.png"/></div>

#### 4. About background blur {docsify-ignore}
Different from STD and HDRP version, in URP you should change background blur weight in ‘Forward Renderer’ asset.
Just increase the ‘Blur Iteration’ and ‘Down Sampling’ value, the higher these two value, more blurred the background is.

!>increase ‘Blur Iteration’ value will give you smooth blurred background but will increase performance cost; increase ‘Blur Iteration’ value will give you low quality block like blur, but will not increase performance cost.

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (14).png"/></div>

### 2-2 Object space version
#### Setup material & solver {docsify-ignore}
Create a new material, change shader type to ‘Custom/RaindropFX/WetSurfaceURP’’;

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (15).png"/></div>

Add ‘Material Linker’ to your model object. ‘Material Linker’ will try to find the target material (main material of your model) automatically, if the component failed to get the correct material or if you changed the material of model after the script have been added, please reset ‘Target Mat’ manually.

<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (16).png"/></div>

Add a droplet texture to ‘Raindrop Tex_alpha’.

<div align=center><img width="60%" src="_pics/RFXHD_300/6.png"/></div>

Now you can see raindrops on your model surface.

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (13).png"/></div>

#### About physical calculation {docsify-ignore}
!>The default physical calculation of RaindropFX is based on the UV space, which means that the water droplets will flow downward along the V-axis of the UV space, that is to say, water droplets' movement depends entirely on the way of UV division.

As shown in the figure below, there are two different UV division methods for the same cylinder model:

<div align=center><img width="80%" src="_pics/RFXP_150/(4).png"/></div>
<div align=center><img width="80%" src="_pics/RFXP_150/(5).png"/></div>

As the figure above shows, left side is the computed raindrop texture. Because of that the flow direction of raindrops is roughly along the v-axis of the UV space, so if we apply the texture to the middle cylinder (with UV division method (a)), the result will be correct; But if we apply the texture to the right cylinder (with UV division method (b)), the result will be wrong.

!>Therefore, in the process of UV division, please try to keep the UV island orientation consistent and try to divide the UV into a whole piece of island.

#### Setup wipe effect {docsify-ignore}
1. Similar with the screen space version, the object space version wipe effect also needs another camera to render a wipe mask. So first you need to create another camera, delete ‘audio listener’, then adjust the view of the camera to matching the wipe area:

<div align=center><img width="60%" src="_pics/RFXHD_300/10.png"/></div>

>Please place the wipe mask camera according to the actual needs. For example, when rendering the windshield's wipe mask, it’s better to set the camera as one of the child of the glass object;

2. Then add a ‘Wipe Camera’ component to the wipe mask camera, drag and drop your glass object (with ‘Material Linker’ component attached) to ‘Linker’ slot, then set ‘Cull Layer’, ‘Mask Size’ and ‘Wipers’ by yourself. Wipers will be automatically moved to the specified cull layer at the beginning of the game. Note that the ‘Mask Size’ property will affects the aspect ratio of the wipe mask captured by the camera. For the sake of rendering performance, the resolution of the wipe mask does not need to be too high;

<div align=center><img width="60%" src="_pics/RFXHD_300/11.png"/></div>

3. Tick the ‘Wipe Effect’ in the ‘Volume’ component, then just run your game.

<div align=center><img width="60%" src="_pics/RFXHD_300/12.png"/></div>

#### About roughness of surface rain material {docsify-ignore}
Different from STD and HDRP version, in URP, final roughness value = material roughness value * roughness value in ‘RFX Blur Pass’：

!>increase ‘Blur Iteration’ value will give you smooth blurred background but will increase performance cost; increase ‘Blur Iteration’ value will give you low quality block like blur, but will not increase performance cost.
<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (14).png"/></div>
<div align=center><img width="60%" src="_pics/RFXU_100/RFXU100_PIC_ (26).png"/></div>

### 2-3 System options
<center>
<table class=44 border=1 cellspacing=0 style="border-collapse:collapse;width:97.2400%;margin-left:5.9500pt;
mso-table-layout-alt:fixed;border:none;mso-border-left-alt:0.5000pt solid rgb(190,190,190);
mso-border-top-alt:0.5000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);
mso-border-insideh:0.5000pt solid rgb(190,190,190);mso-border-insidev:0.5000pt solid rgb(190,190,190);mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;">
			<tr style="height:33.0500pt;">
				<td width=127 valign=top style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:1.0000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(165,165,165);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';color:rgb(0,0,0);
font-weight:bold;font-size:16.0000pt;">Category</span>
						</b><b>
							<span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:16.0000pt;"><o:p></o:p></span>
						</b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:1.0000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(165,165,165);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';color:rgb(0,0,0);
font-weight:bold;font-size:16.0000pt;">Parameter</span>
						</b><b>
							<span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:16.0000pt;"><o:p></o:p></span>
						</b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:1.0000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(165,165,165);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:16.0000pt;">D</span>
						</b><b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';color:rgb(0,0,0);
font-weight:bold;font-size:16.0000pt;">escription</span>
						</b><b>
							<span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:16.0000pt;"><o:p></o:p></span>
						</b>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=8 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Basic Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fadeout_fadein_switch</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Waterdrops will fade in/out automatically if you disable/enable this.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fast mode</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Works with &#8216;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Fadeout_fadein_switch</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8217;. </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Waterdrops will fadeout with higher frame rate but lower accuracy if you </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">turn it on</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">*It will greatly affect the effect of screen fog.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fade speed</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">T</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">he speed of </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">waterdrops </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">fadeout. The bigger, the faster.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Refresh rate</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">For example, if you set it to 2, the raindrop animation will calculate every two frames.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Force rain texture size</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top rowspan=2 style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">W</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">hen turn it on, raindropFX will always calculate the screen rain texture of the specified size(Calc Rain Texture Size) and then rescale it to the current screen resolution size. When your game resolution is very large, opening this option will improve performance.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p>&nbsp;</o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Calc rain texture size</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Down Sampling</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">If you </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">want to make the screen rain </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">texture size follow the screen resolution automatically, turn off </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8216;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">force rain texture size</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8217;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">, </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">then </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">the </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">rain </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">texture size </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">will equals </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">screen resolution * </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">D</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">own</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">S</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">ampling</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Raindrop tex_alpha</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Raindrop texture must be set before you can use RaindropFX. </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Find the</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">raindrop texture</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;at </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8216;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">RaindropFXPro_PPV/Resources/Textures/raindrop_a</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8217;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">. Or you can use your own raindrop texture. </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">*</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">The calculation of the program is based on the alpha channel of the texture, so PNG format images with alpha channel are recommended. </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=4 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Raindrop Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Generate trail</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Controls whether the dynamic water droplets produce a tail when they slide. When the dynamic water droplets produce a static tail drop, itself loses a certain amount of mass, which will affect the results of the physical calculation.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Max static raindrop number</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top rowspan=2 style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Water droplets are divided into two categories: static and dynamic. Static water droplets are generated on the screen at random locations and cannot be moved. Dynamic water droplets are generated by the physical computing movement.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p>&nbsp;</o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Max dynamic raindrop number</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Raindrop size range</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Calculate the size range of raindrops based on your raindrop texture.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=8 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Physical Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Calc time step</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">The time step of physical calculation.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Use wind</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Tick </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">this if you want to use </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">screen </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">wind.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Wind turbulence</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Controls wind turbulence amount.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p>&nbsp;</o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Wind turb scale</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Adjust scale of </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">the </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">wind turbulence.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Wind</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Wind power adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Radial wind</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Enable radial wind, mostly for driving simulation.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Gravity</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Gravity adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:26.6500pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Friction</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Friction adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=3 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Special Post Effects</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Rain Mask_grayscale</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Controlling visible part of droplets based on a grayscale image.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Pixelization</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Enable/Disable droplet pixelization. This effect can be used in pixel style games.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Pix Resolution</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Specifies the pixel resolution. The lower the resolution, the more obvious the pixel of water droplets.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=3 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Interactive Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Mouse Painting</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Enable this and you&#8217;ll be able to painting raindrops on the screen using your mouse. (hold left mouse and drag your mouse)</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Wipe Effect</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">If you want to enable dynamic wipe effect, tick this. (Works with &#8216;Wiper&#8217; component, please refer to chapter 2-1-3 to see how to setup)</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fogging Speed</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">The speed at which the fog on the screen is restored after being </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">wiped. </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">The larger the value, the slower the recovery</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=8 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Rendering Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Tint color</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Tint color for droplets.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Tint</span>
						</b><b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Amount</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">The larger the value, the thicker the color.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Distortion</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Screen blend effect intensity.</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;The larger the value, the stronger the distortion.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">In black</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top rowspan=4 style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Color level parameter</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">s</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Can be used to adjust the </span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8216;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">cutoff</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">&#8217;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;effect of waterdrop edge.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">In white</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Out white</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Out black</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fusion</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Fuse small</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;droplets</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;that are close together into a big one</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=4 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Fog Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Use fog</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">If you want to use screen fog, </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">turn it on</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fog intensity</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Screen fog effect intensity.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Fog tint</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">C</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">olor of fog.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Fog iteration</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Controls the effect of water droplet wake on fog.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=127 valign=top rowspan=5 style="width:95.7000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(255,255,255);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:14.0000pt;">Depth of Field Settings</span>
						</b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:14.0000pt;"><o:p></o:p></span></b>
					</p>
				</td>
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Droplet blur</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Enable this to blur</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;foreground</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">&nbsp;waterdrops.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:10.5000pt;">Blur Iteration</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;">A</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">djust blur strength.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			<tr style="height:31.2000pt;">
				<td width=181 valign=top style="width:135.9500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;">
						<b>
							<span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:10.5000pt;">Focalize</span>
						</b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:10.5000pt;"><o:p></o:p></span>
					</p>
				</td>
				<td width=329 valign=top style="width:247.2500pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);">
					<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;"><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:9.0000pt;">Adjust focal length.</span><span style="font-family:'微软雅黑 Light';font-size:9.0000pt;"><o:p></o:p></span></p>
				</td>
			</tr>
			</tr>
		</table>
	</center>


## 3 Tips

> If you can see the raindrop effect in the editor in play mode but can not see it in a build：

try to go to 'ProjectSettings->Graphics' in your Unity editor then add all the shaders of RaindropFX (located at : RaindropFX_URP/Shaders) to 'always included shaders', then rebuild your game and try it again.

<div align=center><img width="70%" src="_pics/RFXHD_300/20.png"/></div>
<div align=center><img width="70%" src="_pics/RFXU_100/RFXU100_PIC_ (28).png"/></div>

## Support
If you have any questions, comments, or requests for new features, please email me directly at: hztmailbox@gmail.com.

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.