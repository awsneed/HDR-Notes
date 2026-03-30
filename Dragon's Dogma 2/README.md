# Dragon's Dogma 2

TODO: Redo this. Seems similar to Elden Ring, where it's actually fine just needs a brightness of 0 or 1. DD2 however has a hard limit of 1k nits regardless of the maximum and brightness, which is surely a bug since you can set a 4k nit maximum.

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
increase the brightness is to turn the overall game brightness in HDR up.

## Establishing SDR Reference

The brightness setting screen in SDR was used for establishing a reference to
match the HDR presentation to.

Here is a screenshot of that image, captured with a forced HDR10 swapchain via
Special K to showcase how the game looks in SDR on an HDR-enabled Windows system
with the default sRGB transfer curve applied and a paper white / SDR white of
203 nits.
![SDR Brightness Setting Screen](<Dragon's Dogma 2 2026-03-27 20ː21ː44.png>)

For sanity, I'm making a few assumptions and taking a shortcut on the reference.

* D65 White
* sRGB or Power Law 2.2 gamma
* 100 nits white

As the instructions on the setting screen suggest, the image in the middle
should disappear at the default brightness level. We need to reverse-engineer a
reference based on this.

### 203 nits SDR adjustment

For SDR content targeting 100 nits that is being scaled to 203 nits (such as for
use in HDR containers / environments) needs a gamma adjustment in order to
maintain the same perceptual shadow detail. It is between 1.15x and 1.16x gamma
adjustment (2.2 * 1.155 = 2.541). Though sRGB targets 80 nits and not 100 nits,
the difference is small enough and sRGB-targeting games are rare enough that I
have not looked into deriving a specific multiplier for them and just use 1.155
still.

This multiplier will need to be applied regardless of the gamma curve as we are
aiming for 203 nit paper white, so I will apply that now.

![SDR Brightness Setting screen with gamma adjustment applied](<Dragon's Dogma 2 2026-03-27 20ː38ː55.png>)

The image in the center, though much more subtle now, is still clearly visible.
So, it seems likely this image and hopefully the game as a whole are targeting
Gamma 2.2 and not sRGB.

### Gamma 2.2 w/ gamma adjustment

![SDR Brightness Setting screen with 2.2 gamma and a gamma adjustment applied](<Dragon's Dogma 2 2026-03-27 20ː42ː42.png>)

After applying the power law 2.2 gamma curve instead of the sRGB curve, the
center image is indistinguishable from the background on my calibrated TV, and
so I feel that is reasonable to assume that this settings screen was created
targeting power law 2.2 gamma, and that the game as a whole should also be
targeting this.

## Matching HDR to the SDR Reference

![SDR Reference screenshot: Dark and dim medieval room with a candle next to a door, and a window with a glimpse of day outside. The candle and window are near 100% white in SDR, with the edges of the screenshot nearing 0% (black) and providing a good comparison of shadow detail with potential for demonstrating an uncapping in the upper brightness range for the window and candle that HDR would provide](<Dragon's Dogma 2 2026-03-27 21ː11ː45.png>)

This is our reference SDR image with power law 2.2 gamma and an additional gamma
adjustment made to compensate for the increase in brightness to 203 nites.

Here is the same scene with HDR enabled, using an appropriate peak brightness
and the default overall brightness.

![Same scene as the SDR reference screenshot. The window and especially the candle are noticeably brighter, but so is the rest of the image including what appears to be lifted shadow detail.](<Dragon's Dogma 2 2026-03-27 21ː06ː00.png>)

There is lifted shadow detail at the default settings compared to the SDR
reference, so adjustments will need to be made. It does appear to be Real HDR
though and not Fake HDR (inverse tonemapped SDR), as more highlight detail and
less clipping is seen outside through the window.

## TODO: Find the best settings

The HDR tonemapper is incredibly strange in this game IMO, and I have not yet
found settings that match well to the SDR. It's possible that the HDR is just
not intended to be SDR+, and I shouldn't be trying to match it, but you can get
very close by setting the overall brightness to 0 or 1. There is a slightly
elevated black floor at any of the overall brightness settings, but the game
does not have something as simple as an sRGB <-> 2.2 mismatch I think, when you
are comparing them back-to-back and looking at the waveforms.
