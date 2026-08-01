# Dragon's Dogma 2

Similar to Elden Ring and forcing HDR in Unreal. DD2 however has a hard limit of 1k nits regardless of the maximum and brightness, which is surely a bug since you can set a 4k nit maximum.

## HDR Quirks

This game has the following quirks in HDR:

### Bugged Peak Brightness?

Though the HDR setting screen allows you to set a peak brightness of 4k nits,
in-game there seems to be a peak brightness setting of 1k nits maximum set on
the tonemapper. If your peak brightness in the settings screen is below 1k, then
the game does tonemap down to it. It's like it tonemaps to the lesser of 1k and
your chosen peak brightness.

Despite this, there is also a noticeable but slight compression on the upper end
of highlights in interfaces if a peak brightness is set not far above 1k nits.
So it is not completely useless to set it if your display can go above 1k nits,
only somewhat so. May as well set it as you would assuming it works as expected.

### SDR <-> HDR UI Brightness

The UI in HDR appears much dimmer than it does in SDR, and the only way to
increase the brightness is to turn the overall game brightness in HDR up, which makes the images less accurate.

## SDR Reference

The brightness setting screen in SDR was used for lining up a reference to
match the HDR presentation to. To me, it seemed that 2.2 power law gamma OR BT.1886 could be used. The central image on the screen, which is supposed to not be visible if brightness is set currently, was still very faintly visible under 2.2 power law gamma. I decided to go with BT.1886 this time around.

Here's a screensot after applying an additional scale to 203 nits and a gamma adjustment of power 1.155:
![Picture of an SDR-in-HDR scene from the game, containing a dimly lit room in a castle, with a window letting in bright light, a bed to the left with a candle next to it, and a fireplace on the right with a fire. The dynamic range of the view of the outside through the window is heavily compressed](SDR-Target.png)

## HDR Adjustments

Setting the in-game HDR settings to maximum peak brightness (for the sake of analysis and because my TV can do 2320 nits anyway) and minimum black level, then adjusting the overall brightness to 0 and applying a linear scaling from 150 to 203 and then a power 1.155 gamma adjustment produces an image of the same scene that very nearly matches the SDR target in the low and mid range while uncompressing the upper range.

Similarly to forcing HDR in Unreal Engine, I can't seem to find an exact overlapping match in those lower ranges to the SDR target, and the scaling from 150 to 203 is similar as well, so it's possible I haven't figure out the exact process that either engine is using but it's some sort of convention.

![The same scene from the SDR Target, now with in-game HDR turned on. It's largely the same except that the window view is now much brighter and does not look nearly as compressed, and the flames on the candle and the fireplace are brighter as well.](HDR-Result.png)

Without ReShade or som way to enact the 150->203 scaling, you could choose overall brightness 0 or 1 as preferred to step to either side of my result here.
