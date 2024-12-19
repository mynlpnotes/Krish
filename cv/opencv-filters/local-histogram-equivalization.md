# 🟠 Local Histogram Equivalization

**Tile 1 (3x3):**

```
50   50   80  
50   50   80  
200  200  210  
```

***

#### **Step 1: Create the Histogram**

<mark style="color:purple;background-color:purple;">**Count how many times each intensity appears in the tile.**</mark>

| Intensity | Count |
| --------- | ----- |
| 50        | 4     |
| 80        | 2     |
| 200       | 2     |
| 210       | 1     |

Total pixels = 4+2+2+1=94 + 2 + 2 + 1 = 9

***

#### **Step 2: Compute Probability for Each Intensity**

<mark style="color:purple;background-color:purple;">**Probability = Count/Total Pixels**</mark>

| Intensity | Count | Probability                      |
| --------- | ----- | -------------------------------- |
| 50        | 4     | 4/9≈0.4444 / 9 $$\approx$$ 0.444 |
| 80        | 2     | 2/9≈0.2222 / 9 $$\approx$$ 0.222 |
| 200       | 2     | 2/9≈0.2222 / 9 $$\approx$$ 0.222 |
| 210       | 1     | 1/9≈0.1111 / 9 $$\approx$$ 0.111 |

***

#### **Step 3: Calculate the Cumulative Distribution Function (CDF)**

<mark style="color:purple;background-color:purple;">**The CDF is the cumulative sum of probabilities.**</mark>

| Intensity | Probability | CDF                                    |
| --------- | ----------- | -------------------------------------- |
| 50        | 0.444       | 0.4440.444                             |
| 80        | 0.222       | 0.444+0.222=0.6660.444 + 0.222 = 0.666 |
| 200       | 0.222       | 0.666+0.222=0.8880.666 + 0.222 = 0.888 |
| 210       | 0.111       | 0.888+0.111=1.0000.888 + 0.111 = 1.000 |

***

#### **Step 4: Normalize the CDF**

The normalized CDF maps the intensities to a new range.\
For an 8-bit image, the intensity range is \[0, 255].

<mark style="color:purple;background-color:purple;">**New Intensity=CDF×(Max Intensity−Min Intensity)+Min Intensity**</mark>

Here, Min Intensity = 0, Max Intensity = 255.

| Intensity | CDF   | New Intensity |
| --------- | ----- | ------------- |
| 50        | 0.444 | 0.444×255≈113 |
| 80        | 0.666 | 0.666×255≈170 |
| 200       | 0.888 | 0.888×255≈226 |
| 210       | 1.000 | 1.000×255=255 |

***

#### **Step 5: Map Old Intensities to New Values**

Replace each pixel in the original tile with its new intensity based on the table above.

| Original Tile | New Tile    |
| ------------- | ----------- |
| 50 50 80      | 113 113 170 |
| 50 50 80      | 113 113 170 |
| 200 200 210   | 226 226 255 |

***

#### **Final Enhanced Tile:**

```
113   113   170  
113   113   170  
226   226   255  
```

