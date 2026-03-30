# Elden Ring

**TL;DR**: Set Adjust Brightness to 0 or 1. It's actually good I think. Just conservatively graded and the settings are a little unintuitive.

## "Accurate" Settings and What Settings Do

- **Adjust Brightness**: Start at 0, raise to preference or for brighter room.
  - At 0, the game will not output anything over 1k nits. As this approaches 10, this upper limit approach 2k nits, which is the highest Maximum Brightness setting available.
  - It's a scalar in the sense that, increasing this stretches the 1k nit image upward toward the 2k hard limit. Ends up looking very washed out since the whole image is being elevated, making shadows look more greyish. This can seem like an sRGB <-> Power 2.2 gamma mismatch, but I don't believe so.
- **Maximum Brightness**: Set as appropriate. Does actually seem to work for compression if anything gets near this value.
- **Adjust Saturation**: Don't go below 5. Set to preference otherwise. Might just be a scalar with 5 being the reference / 1.0 value, but the UI Blend shader that applies the tonemapping / grading has a full Saturation 10 image internally before said tonemapping. *shrug*
  - **5** = Rec. 709
  - **7** = DCI-P3
  - **10** = Rec. 2020
  - **0** = Greyscale lol
  
## Screenshots

- Adjust Brightness = 1
- Maximum Brightness = 2000
- Adjust Saturation = 10

![alt text](<ELDEN RING 2026-03-30 02ː40ː15.png>)
![alt text](<ELDEN RING 2026-03-30 02ː42ː54.png>)
