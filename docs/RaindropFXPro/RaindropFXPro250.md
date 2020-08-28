# RaindropFX - Pro (2.50)

Easy to use realistic camera lens raindrop animation effects for standard rendering pipeline.

## 1 New Features
### 1-1 Dyniamic wipe effect

<div align=center><img width="70%" src="_pics/RFXP_250/wipe.png"/></div>
<center>Dyniamic wipe effect</center>

### 1-2 Droplet pixelization

<div align=center><img width="70%" src="_pics/RFXP_250/pix.png"/></div>
<center>Create pixel-style water droplets</center>

### 1-3 Screen rain mask

<div align=center><img width="70%" src="_pics/RFXP_250/mask.png"/></div>
<center>Controlling visible part of droplets based on a grayscale image</center>

## 2 Getting started
### 2-1 Screen space version
### 2-1-1 Install post processing stack V2 {docsify-ignore}
!> **Important** The post processing stack (v2) must be installed before you can continue.

- <strong>For SRP in Unity 2018.4+</strong>

Since version 2018.4, HDRP and URP using their built-in post-processing stack instead of PPV2, current version of RaindropFX only support standard rendering pipeline so can't be used in HDRP and URP in Unity 2018.4+. 
You can find RaindropFX Pro for HDRP here: http://u3d.as/1Un5. URP version will be released in the near future.

- <strong>For standard pipeline in Unity 2018.2+ and SRP in Unity 2018.2-2018.3</strong>

If you create your project using HDRP or LWRP template, PPV2 will be included in your project automatically, you do not need to do anything. Otherwise, you need to use the Package Manager to install the PPV2 :

<div align=center><img width="70%" src="_pics/RFXP_250/packageMgr.png"/></div>

- <strong>For unity 2018.1 or lower</strong>

If you want to use RaindropFX in those old versions unity, please using lite version: http://u3d.as/14V0.

### 2-1-2 Download RaindropFX to your project {docsify-ignore}
If you have an old version RaindropFX, delete it first, then download and import new RaindropFX to your project, and you will see those files:

<div align=center><img width="20%" src="_pics/RFXP_250/files.png"/></div>

### 2-1-3 Post processing stack setup {docsify-ignore}
#### 1. Camera setup
Select the main camera in your secne, and add a "Post Process Layer" script component. On the component, in the "Layer" dropdown, select the "PostProcessing" layer.

#### 2.Post process volume Setup
Go to "GameObject -> 3D Object -> Post-process Volume" to create a new volume object. On the "Post Process Volume" component, tick the "Global" box, then choose a profile in the profile field or create a new profile.

#### 3.Post process profile setup
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> CameraLensRain" to add the effect.

### 2-2 Setup wipe effect
1. Add 'Wiper' component to your main camera;

<div align=center><img width="80%" src="_pics/RFXP_250/wipe1.png"/></div>

2. Add 'Post-Process Volume' component to 'Post Volumn', then add all the wipers to 'Wipers' (you can set the size of the 'Wipers' to any number you like. For example, if you want to use two wipers, set it to 2, then drag and drop your wipers into the slots);

<div align=center><img width="80%" src="_pics/RFXP_250/wipe2.png"/></div>

3. Then tick the 'Wipe Effect' and 'Wiper' in the 'Raindrop FX_PPV' in the 'Post-Process Volume'. Just leave the 'Wiper' empty, it'll be assigned by 'Wiper' component automatically;

<div align=center><img width="40%" src="_pics/RFXP_250/wipe3.png"/></div>

4. Finally, run your game and drag your wiper, you'll see the wipe effect. The wipe effect affects both water droplets and the screen fog.

### 2-3 Object space version
!> **NOTE** The current version of object space RaindropFX is a non-physical accurate version. Physical calculation of water droplets are totally dependent on the UV space of your model.
So the way of dividing the UV will directly affect the flow of water droplets. 

### 2-3-1 Setup your model {docsify-ignore}
As shown in the figure below, there are two different UV division methods for the same cylinder model:

<div align=center><img width="80%" src="_pics/RFXP_150/(4).png"/></div>
<div align=center><img width="80%" src="_pics/RFXP_150/(5).png"/></div>

As the figure above shows, left side is the computed raindrop texture. Because of that the flow direction of raindrops is roughly along the v-axis of the UV space, 
so if we apply the texture to the middle cylinder (with UV division method (a)), the result will be correct; 
But if we apply the texture to the right cylinder (with UV division method (b)), the result will be wrong.

!> **IMPORTANT** Therefore, in the process of UV division, 
please try to keep the UV island orientation consistent and try to divide the UV into a whole piece of island. 

### 2-3-2 Setup material & solver {docsify-ignore}
1. Create a material for your model, change the shader type to 'Custom/RaindropFX/WetSurface';

<div align=center><img width="50%" src="_pics/RFXP_200/shader.png"/></div>

2. Add 'Material Linker' to your model. 
'Material Linker' will try to find the target material (main material of your model) automatically, 
if the component failed to get the correct material or if you changed the material of model after scripts have been added, please reset 'Target Mat' manually.

<div align=center><img width="50%" src="_pics/RFXP_200/target.png"/></div>

3. Now you can see raindrops on your model surface.

<div align=center><img width="60%" src="_pics/RFXP_200/objectSpaceVer.png"/></div>

## 3 System options
<center>
<table class=MsoTableGrid border=1 cellspacing=0 style="border-collapse:collapse;width:446.1000pt;mso-table-layout-alt:fixed;
border:none;mso-border-left-alt:0.5000pt solid windowtext;mso-border-top-alt:0.5000pt solid windowtext;
mso-border-right-alt:0.5000pt solid windowtext;mso-border-bottom-alt:0.5000pt solid windowtext;mso-border-insideh:0.5000pt solid windowtext;
mso-border-insidev:0.5000pt solid windowtext;mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;">
	<tr style="height:46.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:1.0000pt solid rgb(0,0,0);mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(0,0,0);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);
font-weight:bold;font-size:20.0000pt;color:rgb(255,255,255);">Parameter</span>
				</b><b>
					<span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:20.0000pt;color:rgb(255,255,255);"><o:p></o:p></span>
				</b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:1.0000pt solid rgb(0,0,0);mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(0,0,0);">
			<p class=MsoNormal align=center style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:center;">
				<b>
					<span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,255,255);font-weight:bold;
font-size:20.0000pt;color:rgb(255,255,255);"><o:p>&nbsp;</o:p></span>
				</b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Fadeout_fadein_switch</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Waterdrops will fade in/out automatically if you disable/enable this.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Fast mode</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Works with &#8216;</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Fadeout_fadein_switch</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&#8217;. </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Waterdrops will fadeout with higher frame rate but lower accuracy if you </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">turn it on</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,0,0);
font-size:10.5000pt;">*It will greatly affect the effect of screen fog.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Fade speed</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">T</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">he speed of </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">waterdrops </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">fadeout. The bigger, the faster.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Raindrop tex_alpha</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Raindrop texture must be set before you can use RaindropFX. </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Find the</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">raindrop texture</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;at &#8220;RaindropFXPro_PPV/Resources/Textures/raindrop_a&#8221;</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">. Or you can use your own raindrop texture. </span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<span style="font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,0,0);font-size:10.5000pt;">*</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,0,0);
font-size:10.5000pt;">The calculation of the program is based on the alpha channel of the texture, so PNG format images with alpha channel are recommended.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Rain Mask_grayscale</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Controlling visible part of droplets based on a grayscale image.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Pixelization</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Enable/Disable droplet pixelization. This effect can be used in pixel style games.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Pix Resolution</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Specifies the pixel resolution. The lower the resolution, the more obvious the pixel of water droplets.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Wipe Effect</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:1.0000pt solid rgb(0,0,0);mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(255,255,255);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">E</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">nable/Disable wipe effect.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Wiper</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:1.0000pt solid rgb(0,0,0);mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(216,216,216);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">T</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">ick this option if you want to enable wipe effect. </span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p><p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';color:rgb(255,0,0);
font-size:10.5000pt;">*there's no need to assign texture/object here.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Force rain texture size</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top rowspan=2 style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">W</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">hen turn it on, raindropFX will always calculate the screen rain texture of the specified size(Calc Rain Texture Size) and then rescale it to the current screen resolution size. When your game resolution is very large, opening this option will improve performance.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Calc rain texture size</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Calc time step</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">The time step of physical calculation.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Refresh rate</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">For example, if you set it to 2, the raindrop animation will calculate every two frames.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Generate trail</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Controls whether the dynamic water droplets produce a tail when they slide. When the dynamic water droplets produce a static tail drop, itself loses a certain amount of mass, which will affect the results of the physical calculation.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Max static raindrop number</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top rowspan=2 style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Water droplets are divided into two categories: static and dynamic. Static water droplets are generated on the screen at random locations and cannot be moved. Dynamic water droplets are generated by the physical computing movement.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Max dynamic raindrop number</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Raindrop size range</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Calculate the size range of raindrops based on your raindrop texture.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Tint color</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal align=justify style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:none;
text-align:justify;text-justify:inter-ideograph;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Tint color for droplets.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Tint weight</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">The larger the value, the thicker the color.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Use wind</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Tick </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">this if you want to use </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">screen </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">wind.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Wind turbulence</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Controls wind turbulence amount.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Wind turb scale</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Adjust scale of </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">the </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">wind turbulence.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Wind</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Wind power adjustment.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Radial wind</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Enable radial wind, mostly for driving simulation.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Gravity</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Gravity adjustment.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Friction</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Friction adjustment.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Distortion</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Screen blend effect intensity.</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;The larger the value, the stronger the distortion.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Use fog</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">If you want to use screen fog, </span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">turn it on</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Fog intensity</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Screen fog effect intensity.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;"></span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;">Fog</span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">&nbsp;iteration</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Controls the effect of water droplet wake on fog.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Edge softness</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Edge softness of water droplets.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">In black</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top rowspan=4 style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid windowtext;
mso-border-bottom-alt:0.5000pt solid windowtext;background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Color level parameter</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">s</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p><p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Can be used to adjust the &#8220;cutoff&#8221; effect of waterdrop edge.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">In white</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Out white</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Out</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"></span></b><b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">black</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Droplet blur</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Enable this to blur</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;foreground</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;waterdrops.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Focalize</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Adjust focal length.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Blur iteration</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Adjust blur strength.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Show steps</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(231,231,231);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Show</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;calculation</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;steps</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;of screen rain texture</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
	<tr style="height:31.2000pt;">
		<td width=218 valign=top style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(0,0,0);
mso-border-left-alt:1.0000pt solid rgb(0,0,0);border-right:1.0000pt dotted windowtext;mso-border-right-alt:1.0000pt dotted windowtext;
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;">
				<b>
					<span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;
font-size:12.0000pt;">Debug log</span>
				</b><b><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-weight:bold;font-size:12.0000pt;"><o:p></o:p></span></b>
			</p>
		</td>
		<td width=349 valign=top style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(0,0,0);mso-border-right-alt:1.0000pt solid rgb(0,0,0);
border-top:none;mso-border-top-alt:1.0000pt solid rgb(0,0,0);border-bottom:1.0000pt solid rgb(0,0,0);
mso-border-bottom-alt:1.0000pt solid rgb(0,0,0);background:rgb(255,255,255);">
			<p class=MsoNormal style="margin-top:0.0000pt;margin-bottom:0.0000pt;mso-pagination:widow-orphan;
text-align:left;"><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">Enable this if you want to see debug info.</span><span style="mso-spacerun:'yes';font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;">&nbsp;Usually do not need to tick.</span><span style="font-family:'Î¢ÈíÑÅºÚ Light';font-size:10.5000pt;"><o:p></o:p></span></p>
		</td>
	</tr>
</table>
</center>


## 4 Bonus content

### 4-1 Batch image renderer
The processing flow of Batch Image Renderer is as follows :
1. 'Batch Sequence Renderer' can be used to render your custom sequence frames to the screen in order;
2. Then you can further applying other post-processing stacks to the input sequence frames; 
3. Finally, you can use the 'Screen Shoter' to save the processed sequence to your local disk.

### 4-1-1 Import your image sequence {docsify-ignore}
First, put all your pictures into 'Assets/Resources/Pictures', if this folder does not exist, create it :

<div align=center><img width="30%" src="_pics/RFXP_150/(7)-3.png"/></div>

### 4-1-2 Setup 'Batch Sequence Renderer' {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Batch Sequence Renderer" to add the renderer :

<div align=center><img width="60%" src="_pics/RFXP_150/(7)-4.png"/></div>

'interval' means that each frame of your input sequence will be rendered to the screen in every n frames.

!> **IMPORTANT** This tool will only start when you click the 'Run' button.

<div align=center><img width="20%" src="_pics/RFXL/5.png"/></div>

!> **NOTE** If you want to render raindrop effects to input sequence, when 'interval' is set to a small value (e.g. 1), 
the water droplets on the output frames will looks like the same because the interval between each frame is too small, 
which will leads to very small time steps in physical calculations. 
So if you want to make a significant change in the state of the water drops on each frame, increase the 'interval' value.

### 4-1-3 Applying other post effects {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX" to add other post effects you prefer. 
All the effects you added will be applied to the input sequence.

### 4-1-4 Setup 'Screen shoter' {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Screen Shoter" to add the screen shoter :

<div align=center><img width="60%" src="_pics/RFXP_150/(7)-5.png"/></div>

The image will be captured in every 'interval' frames and the 
captured images will be saved to the 'Assets/StreamingAssets/Output' folder automatically :

<div align=center><img width="80%" src="_pics/RFXP_150/(7)-6.png"/></div>

!> **IMPORTANT** This tool will only start when you click the 'Run' button. 

### 4-1-5 Sorting post effects {docsify-ignore}
First, keep the value of 'interval' in both 'Batch Sequence Renderer' and 'Screen Shoter' as the same. Then, on the "Post Process Layer" component, 
sort after stacks manually, please make sure that 'Batch Sequence Renderer' is at the top, 'Screen Shoter' is at bottom.

<div align=center><img width="60%" src="_pics/RFXP_150/(7)-7.png"/></div>

<div align=center><img width="60%" src="_pics/RFXP_150/(7)-8.png"/></div>

Finally, run the game and all the input images in the 'Pictures' folder will be applied with post-effects you have been added before being output to the 'Output' folder.

### 4-2 Bonus post stacks
### 4-2-1 Screen blur effect {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Blur" to add the blur effect :
<div align=center><img width="70%" src="_pics/RFXP_150/(12).png"/></div>
It can blur your screen based on Gaussian Blur :
<div align=center><img width="70%" src="_pics/RFXP_150/(13).png"/></div>
<center>Without blur effect</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(14).png"/></div>
<center>With blur effect</center>

### 4-2-2 Ground glass effect {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Screen Blend" to add the screen blend effect :
<div align=center><img width="70%" src="_pics/RFXP_150/(15).png"/></div>
It can create ground glass effect based on your Height Map/Normal Map, and can achieve color mixing effects based on your Color Map :
<div align=center><img width="70%" src="_pics/RFXP_150/(16).png"/></div>
<center>Without screen blend effect</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(17).png"/></div>
<center>With screen blend effect</center>

### 4-2-3 Multi-player split screen {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Split Screen" to add the split screen effect :
<div align=center><img width="70%" src="_pics/RFXP_150/(18).png"/></div>
Then you should create another camera for player2 and create an render texture for camera2 as render target :
<div align=center><img width="70%" src="_pics/RFXP_150/(19).png"/></div>
<center>Set render texture size to as same as your main camera</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(20).png"/></div>
<center>Drag and drop the render texture to target texture of your camera2</center>

<div align=center><img width="40%" src="_pics/RFXP_150/(21).png"/></div>
<center>Use an grayscale map as split mask, white part is the camera view of player2</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(22).png"/></div>
<center>Without split screen effect</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(23).png"/></div>
<center>With split screen effect</center>

### 4-2-4 Color level effect {docsify-ignore}
On the "Post Process Volume" component, go to "Add effect -> RaindropFX -> Color Level" to add the color level effect :
<div align=center><img width="70%" src="_pics/RFXP_150/(24).png"/></div>
<div align=center><img width="70%" src="_pics/RFXP_150/(25).png"/></div>
<center>Without color level effect</center>
<div align=center><img width="70%" src="_pics/RFXP_150/(26).png"/></div>
<center>With color level effect</center>

## Support
If you have any questions, comments, or requests for new features, please email me directly at: hztmailbox@gmail.com.

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.