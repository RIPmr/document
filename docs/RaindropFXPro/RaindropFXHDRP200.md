# RaindropFX Pro HDRP (2.00)

Easy to use realistic camera lens raindrop animation effects for new HDRP 7.1.8+.

## 1 New Features
### 1-1 Object space enhancement
<br>
<div align=center><img width="70%" src="_pics/RFXHD_200/objectSpace.png"/></div>
<center>Detail Enhanced Object Space Version</center>

## 2 Getting started
### 2-1 Screen space version
### 2-1-1 Download and configure RaindropFX {docsify-ignore}
!> **Important** If you have any old version RaindropFX, delete it first.

Download and import new RaindropFX to your project, and you will see those files:

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (1).png"/></div>

Then, go to ‘Edit/Project Settings...’, add RaindropFX to ‘After Post Process’:

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (2).png"/></div>

### 2-1-2 Post processing stack setup {docsify-ignore}
#### 1. Volume setup
Select any object in your scene, and add a “Volume” component.

<div align=center><img width="50%" src="_pics/RFXHD_200/hd (3).png"/></div>

#### 2.RaindropFX Setup
On the ‘Volume’ component, choose a profile in the profile field or create a new profile, then click ‘Add Override’, go to “Post-processing -> RaindropFX -> RaindropFX_HDRP” to add the raindrop effect.

<div align=center><img width="50%" src="_pics/RFXHD_200/hd (4).png"/></div>

Raindrop texture must be set before you can use RaindropFX. Find the raindrop texture at “RaindropFXPro_HDRP/Resources/Textures/raindrop_a”. Or you can use your own raindrop texture.

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (5).png"/></div>

Now you can see the raindrop effect in your scene.

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (6).png"/></div>

### 2-2 Object space version
!> **NOTE** The current version of object space RaindropFX is a non-physical accurate version. Physical calculation of water droplets are totally dependent on the UV space of your model.
So the way of dividing the UV will directly affect the flow of water droplets. 

### 2-2-1 Setup your model {docsify-ignore}
As shown in the figure below, there are two different UV division methods for the same cylinder model:

<div align=center><img width="80%" src="_pics/RFXP_150/(4).png"/></div>
<div align=center><img width="80%" src="_pics/RFXP_150/(5).png"/></div>

As the figure above shows, left side is the computed raindrop texture. Because of that the flow direction of raindrops is roughly along the v-axis of the UV space, 
so if we apply the texture to the middle cylinder (with UV division method (a)), the result will be correct; 
But if we apply the texture to the right cylinder (with UV division method (b)), the result will be wrong.

!> **IMPORTANT** Therefore, in the process of UV division, 
please try to keep the UV island orientation consistent and try to divide the UV into a whole piece of island. 

### 2-2-2 Setup material & solver {docsify-ignore}
1. Create a material for your model, change the shader type to 'Custom/RaindropFX/WetSurface_HDRP';

<div align=center><img width="60%" src="_pics/RFXHD_200/hd (11).png"/></div>

2. Add ‘Material Linker’ to your model object. ‘Material Linker’ will try to find the target material (main material of your model) automatically, if the component failed to get the correct material or if you changed the material of model after the script have been added, please reset ‘Target Mat’ manually.

<div align=center><img width="60%" src="_pics/RFXHD_200/hd (12).png"/></div>

3. Add a droplet texture to ‘Raindrop Tex_alpha’.

4. Now you can see raindrops on your model surface.

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (13).png"/></div>

## 3 System options
<center>
<table class=43  border=1  cellspacing=0  style="border-collapse:collapse;width:426.1000pt;mso-table-layout-alt:fixed;
border:none;mso-border-left-alt:0.5000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);
mso-border-right-alt:0.5000pt solid rgb(190,190,190);mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);mso-border-insideh:0.5000pt solid rgb(190,190,190);
mso-border-insidev:0.5000pt solid rgb(190,190,190);mso-padding-alt:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;" ><tr style="height:46.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:1.0000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(165,165,165);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';color:rgb(0,0,0);
font-weight:bold;font-size:20.0000pt;" >Parameter</span></b><b><span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:20.0000pt;" ><o:p></o:p></span></b></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:1.0000pt solid rgb(190,190,190);mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(165,165,165);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:20.0000pt;" >D</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';color:rgb(0,0,0);
font-weight:bold;font-size:20.0000pt;" >escription</span></b><b><span style="font-family:'微软雅黑 Light';color:rgb(0,0,0);font-weight:bold;
font-size:20.0000pt;" ><o:p></o:p></span></b></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fadeout_fadein_switch</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Waterdrops will fade in/out automatically if you disable/enable this.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fast mode</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Works with &#8216;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Fadeout_fadein_switch</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&#8217;. </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Waterdrops will fadeout with higher frame rate but lower accuracy if you </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >turn it on</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >*It will greatly affect the effect of screen fog.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fade speed</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >T</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >he speed of </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >waterdrops </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >fadeout. The bigger, the faster.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Raindrop tex_alpha</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Raindrop texture must be set before you can use RaindropFX. </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Find the</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >raindrop texture</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;at &#8220;RaindropFXPro_PPV/Resources/Textures/raindrop_a&#8221;</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >. Or you can use your own raindrop texture. </span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >*</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >The calculation of the program is based on the alpha channel of the texture, so PNG format images with alpha channel are recommended. </span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Force rain texture size</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  rowspan=2  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >W</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >hen turn it on, raindropFX will always calculate the screen rain texture of the specified size(Calc Rain Texture Size) and then rescale it to the current screen resolution size. When your game resolution is very large, opening this option will improve performance.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Calc rain texture size</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Calc time step</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >The time step of physical calculation.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Refresh rate</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >For example, if you set it to 2, the raindrop animation will calculate every two frames.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Generate trail</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Controls whether the dynamic water droplets produce a tail when they slide. When the dynamic water droplets produce a static tail drop, itself loses a certain amount of mass, which will affect the results of the physical calculation.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Max static raindrop number</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  rowspan=2  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Water droplets are divided into two categories: static and dynamic. Static water droplets are generated on the screen at random locations and cannot be moved. Dynamic water droplets are generated by the physical computing movement.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Max dynamic raindrop number</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Raindrop size range</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Calculate the size range of raindrops based on your raindrop texture.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >T</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >int color</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Tint color for droplets.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Tint weight</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >The larger the value, the thicker the color.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Use wind</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Tick </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >this if you want to use </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >screen </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >wind.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Wind turbulence</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Controls wind turbulence amount.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Wind turb scale</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Adjust scale of </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >the </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >wind turbulence.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Wind</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Wind power adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >R</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >adial wind</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Enable radial wind, mostly for driving simulation.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Gravity</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Gravity adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Friction</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Friction adjustment.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Distortion</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Screen blend effect intensity.</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;The larger the value, the stronger the distortion.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Use fog</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >If you want to use screen fog, </span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >turn it on</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fog intensity</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Screen fog effect intensity.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >F</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >og tint</span></b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >C</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >olor of fog.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fo</span></b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >g</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >&nbsp;iteration</span></b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Controls the effect of water droplet wake on fog.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Fusion</span></b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" ><o:p></o:p></span></b></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Fuse small</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;droplets</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;that are close together into a big one</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >In black</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  rowspan=4  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:none;border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Color level parameter</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >s</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Can be used to adjust the &#8220;cutoff&#8221; effect of waterdrop edge.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >In white</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Out white</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:31.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Out</span></b><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >&nbsp;</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >black</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:35.7000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Droplet blur</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Enable this to blur</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;foreground</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >&nbsp;waterdrops.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:81.2500pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="font-family:'微软雅黑 Light';font-weight:bold;font-size:12.0000pt;" >I</span></b><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >nvert blur</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" >S</span><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >witch between background blur and foreground droplet blur.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:38.5000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Focalize</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Adjust focal length.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:37.2000pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Blur iteration</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);background:rgb(241,241,241);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Adjust blur strength.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr><tr style="height:39.3500pt;" ><td width=218  valign=top  style="width:163.8000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:1.0000pt solid rgb(190,190,190);
mso-border-left-alt:0.5000pt solid rgb(190,190,190);border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><b><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-weight:bold;
font-size:12.0000pt;" >Edge softness</span></b><span style="font-family:'微软雅黑 Light';font-weight:normal;font-size:12.0000pt;" ><o:p></o:p></span></p></td><td width=349  valign=top  style="width:262.3000pt;padding:0.0000pt 5.4000pt 0.0000pt 5.4000pt ;border-left:none;
mso-border-left-alt:none;border-right:1.0000pt solid rgb(190,190,190);mso-border-right-alt:0.5000pt solid rgb(190,190,190);
border-top:none;mso-border-top-alt:0.5000pt solid rgb(190,190,190);border-bottom:1.0000pt solid rgb(190,190,190);
mso-border-bottom-alt:0.5000pt solid rgb(190,190,190);" ><p class=MsoNormal  style="margin-top:0.0000pt;margin-bottom:0.0000pt;" ><span style="mso-spacerun:'yes';font-family:'微软雅黑 Light';font-size:10.5000pt;" >Edge softness of depth effect.</span><span style="font-family:'微软雅黑 Light';font-size:10.5000pt;" ><o:p></o:p></span></p></td></tr></table>
</center>


## 4 Tips

> If you can see the raindrop effect in the editor in play mode but can not see it in a build：

try to go to 'ProjectSettings->Graphics' in your Unity editor then add all the shaders of RaindropFX (located at : RaindropFX_HDRP/Shaders) to 'always included shaders', then rebuild your game and try it again.

<div align=center><img width="80%" src="_pics/RFXHD_200/hd (15).png"/></div>

## Support
If you have any questions, comments, or requests for new features, please email me directly at: hztmailbox@gmail.com.

</br>
</br>

Welcome to visit my homepage: https://huanime.com.cn/.