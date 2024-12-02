# CLAHE

CLAHE is a contrast enhancement technique that improves upon Histogram Equalization by focusing on local image regions and addressing noise amplification issues.

***

**Steps in CLAHE**

1. **Divide the Image into Tiles**
   * Split the image into non-overlapping small regions (e.g., 8x8 or 16x16 tiles).
2. **Local Histogram Equalization**
   * Compute the histogram of pixel intensities for each tile.
   * Redistribute pixel intensities using Histogram Equalization to enhance contrast.
3. **Contrast Limiting**
   * Limit the maximum intensity bin height in the histogram using a **clip limit**.
   * Redistribute excess counts evenly across other bins to prevent noise over-amplification.
4. **Interpolate to Avoid Artifacts**
   * Smoothly merge neighboring tiles using bilinear interpolation to avoid boundary artifacts.
5. **Output**
   * The final image has locally enhanced contrast while reducing noise.

***

**Key Parameters**

1. **Tile Size**
   * Determines the size of the local regions for contrast enhancement.
   * Smaller tiles increase local detail but may introduce noise.
2. **Clip Limit**
   * Sets the threshold for contrast limiting.
   * Higher clip limits allow more contrast enhancement but risk noise amplification.
3. **Interpolation**
   * Ensures smooth transitions between tiles, avoiding visible seams.

***

**Advantages**

* Enhances contrast in local regions.
* Reduces over-amplification of noise compared to standard Histogram Equalization.
* Suitable for low-contrast images.

***

**Applications**

* **Medical Imaging**: Highlighting details in X-rays and CT scans.
* **Satellite Imaging**: Enhancing poorly lit regions in photos.
* **Night Vision Cameras**: Improving clarity in dark conditions.

***

**Compact Table Summary**

| **Step**                | **Description**                                    |
| ----------------------- | -------------------------------------------------- |
| Divide Image into Tiles | Split into small regions (e.g., 8x8 tiles).        |
| Local Histogram Equal.  | Equalize histograms for individual tiles.          |
| Contrast Limiting       | Clip excess histogram values to reduce noise.      |
| Interpolation           | Merge tiles smoothly using bilinear interpolation. |
| Final Image             | Enhanced contrast with reduced noise.              |
