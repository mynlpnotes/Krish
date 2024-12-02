# HSV Histogram

### Hue Histogram

* Hue represents the color type in the HSV color space (e.g., red, blue, green). In OpenCV, the range of hue values is scaled from 0 to 180 (corresponding to 0° to 360° on a color wheel).
* In OpenCV, Hue (H) is scaled to a range of 0 to 179 instead of 0 to 360 to accommodate the fact that OpenCV stores HSV values as 8-bit integers (with a range of 0-255).
* Hue range is halved (i.e., 360° / 2 = 179)

**Key Points:**

* Peaks in Hue: <mark style="color:purple;background-color:purple;">**The spikes in the histogram indicate the dominance of specific hues (colors) in the image. For example, a spike around 120 corresponds to cyan, while 0/180 corresponds to red.**</mark>
* Flat Distribution: A relatively flat histogram means the image contains a wide variety of colors.
* Narrow Distribution: A narrow distribution with a prominent peak means that the image has a predominant color.

### Saturation Histogram

* Saturation indicates the intensity or purity of colors. The range is from 0 to 255, where:
  * <mark style="color:purple;background-color:purple;">**Low values (close to 0) represent more muted, washed-out colors (grays, pastels).**</mark>
  * <mark style="color:purple;background-color:purple;">**High values (closer to 255) represent vivid, saturated colors (rich reds, blues, etc.).**</mark>

**Key Points:**

* High Saturation Values: If the histogram has significant values in the higher range (toward 255), this indicates that the image contains vibrant, highly saturated colors.
* Low Saturation Values: A histogram skewed toward lower values means the image has more muted or pastel-like colors. Images with low saturation may look more grayish or have faded colors.

### Value (Brightness) Histogram

* Value represents the brightness or luminance of the image. Like saturation, its range is from 0 to 255, where:
  * <mark style="color:purple;background-color:purple;">**Low values (near 0) mean darker pixels (shadows, black areas).**</mark>
  * <mark style="color:purple;background-color:purple;">**High values (near 255) mean brighter pixels (highlights, white areas).**</mark>

**Key Points:**

* Peaks in the Lower Range: If you see a peak toward the left of the histogram (lower values), the image has a lot of dark regions (shadows, low-light areas).
* Peaks in the Higher Range: A peak toward the right indicates that the image contains many bright regions (sunlit areas, light sources).
* Balanced Distribution: A balanced histogram spread across the value range suggests that the image contains a good balance between bright, dark, and mid-tones.

### Summary

* Hue (H): 0 to 179
* Saturation (S): 0 to 255
* Value (V): 0 to 255
* Hue Histogram: The peaks may show around the yellow/orange range (30-60), as sunsets have warm tones. You may also see secondary peaks for the blue sky (around 120).
* Saturation Histogram: You may see values both low and high. The sky might be desaturated (less intense), while the setting sun and clouds could have vivid orange hues (high saturation).
* Value Histogram: Expect more balanced values. The sky might be bright, so there will be some peaks toward the right (higher brightness), but the ground and shadows in the landscape might push some values toward the lower end.

### Interpretation

* Vibrant Image (e.g., flowers, neon lights): Expect high saturation, balanced hue distribution, and brightness across the entire range.
* Muted Image (e.g., foggy scene): Low saturation and low to mid-brightness. The hue histogram might show fewer colors.
* Overexposed Image (e.g., too much sunlight): Brightness histogram will peak near the right end, suggesting loss of detail in highlights.
* Underexposed Image (e.g., low-light room): Brightness histogram will peak near the left end, indicating loss of detail in shadows.
