# Color Model

A color model is a mathematical model that describes the way colors can be represented as a set of numbers.

* <mark style="color:purple;background-color:purple;">**Pillow used RGB**</mark>
* <mark style="color:purple;background-color:purple;">**OpenCV uses BGR**</mark>

1. **RGB (Red, Green, Blue)**

* <mark style="color:purple;background-color:purple;">**An additive color model, where colors are formed by adding red, green, and blue light in varying intensities.**</mark>
* Each pixel is represented by three values: red, green, and blue, ranging from 0 to 255.

2. **CMYK (Cyan, Magenta, Yellow, Black)**&#x20;

* Not used in CV
* A subtractive color model, commonly used in printing.
* Colors are created by subtracting colors from white light using cyan, magenta, yellow, and black inks.

3. **HSV (Hue, Saturation, Value)**

* A color model that represents color in terms of hue, saturation, and value.
* Hue: The color tone
* Saturation: The purity of the color
* Value: The brightness or intensity of the color.

4. **HSL (Hue, Saturation, Lightness)**

* Similar to HSV, but uses lightness instead of value.
* Lightness represents the overall brightness of the color.

5. **YIQ**

* A color model used in analog color television systems
* It separates the luminance (Y)(brightness or intensity of a color) component from the chrominance (I and Q)(hue and saturation of a color) components.
