# Elden Ring

**TL;DR**: Set Adjust Brightness to 2. It's actually good I think. Just conservatively graded and the settings are a little unintuitive.

## "Accurate" Settings and What Settings Do

- **Adjust Brightness**: Set to 2 to start with. Adjust as preferred.
  - At 0, the game will not output anything over 1k nits. As this approaches 10, this upper limit approach 2k nits, which is the highest Maximum Brightness setting available.
  - It's a scalar in the sense that, increasing this stretches the 1k nit image upward toward the 2k hard limit. As you approach 10 it ends up looking very washed out since the whole image is being elevated, making shadows look more greyish. This can seem like there is an sRGB <-> Gamma 2.2 mismatch, but the game actually is fine in that regard and matches a BT.1886 / Gamma 2.4 EOTF at Brightness 2. Ideally it just needs an additional 1.155 gamma adjustment on top of that and it's perfect.
- **Maximum Brightness**: Set as appropriate. Does actually seem to work for compression if anything gets near this value, but also see the Adjust Brightness setting above for an explanation of what your actual effective peak brightness will be.
- **Adjust Saturation**: Don't go below 5. Set to preference otherwise. Might just be a scalar with 5 being the reference / 1.0 value, but the UI Blend shader that applies the tonemapping / grading has a full Saturation 10 image internally before said tonemapping. *shrug*
  - **5** = Rec. 709
  - **7** = DCI-P3
  - **10** = Rec. 2020
  - **0** = Greyscale lol

## SDR Target

Using the SDR brightness setting menu to line-up the image, I think BT.1886 or Gamma 2.2 are both appropriate. I went with BT.1886, and in HDR at Adjust Brightness = 2, the game very closely matches a 100 -> 203 nit scaled BT.1886 image. From there I also applied said scaling and the typical SDR -> HDR gamma adjustment of 1.155.

![SDR-in-HDR screenshot with analysis overlay of one of the starting areas, just before reaching the surface of the world.](SDR-Target.png)

## HDR Adjustments

As noted above, I set the Adjust Brightness setting to 2 and the Maximum Brightness setting to 2000. For these screenshots I left saturation at 5, but I like to play around with it between 5 and 10. 5 matches SDR and so is probably the most accurate though. After that, all I needed to do was apply a gamma adjustment of power 1.155, and the image is not a perfect match for SDR in the lower and mid ranges, but it is very close, acceptably so I think.

![The same scene from the SDR Target, now with in-game HDR turned on and the adjustments applied. It's practically the same in most areas, but the flames of some torches on the walls are noticeably brighter and have more detail compared to in SDR.](HDR-Result.png)
