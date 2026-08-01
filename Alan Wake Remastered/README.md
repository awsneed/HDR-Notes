# Alan Wake Remastered 👍

This game has one of the best HDR implementations.

## SDR Reference

The SDR reference was lined-up using the in-game brightness setting screen, which seemed to indicate a 2.2 power law gamma EOTF target. After correcting for that, a linear scaling up to 203 nits from 80 and a 1.155 power gamma adjustment were applied.

![SDR-in-HDR screenshot of the game's main menu, to be the reference for adjusting HDR](SDR-Target.png)

## HDR Adjustments

After switching the game's HDR on, only the 1.155 power gamma adjustment need be applied to line up practically perfectly with the SDR reference! This means the game correctly scales to 203 nits and applies a 2.2 power law gamma EOTF to its scRGB output!

![HDR screenshot fo the game's main menu, now with the game's HDR turned on. It is an extremely good match for the SDR reference in the low and mid tone regions, while displaying an uncompressed upper range](HDR-Result.png)

Very enthusiastic thank you to [d3t](https://d3tltd.com/) for remastering this game and adding in such a nice HDR implementation years later.
