# 🟢 Convert RGB to HSV

Using an algorithm we can convert RGB to HSV:

1. Divide r,g,b by 255
2. Compute cmax, cmin, difference
3. Hue calculation :

* if cmax and cmin are equal, then h = 0
* if cmax equal r then compute h = (60 \* ((g – b) / diff) + 360) % 360
* if cmax equal g then compute h = (60 \* ((b – r) / diff) + 120) % 360
* if cmax equal b then compute h = (60 \* ((r – g) / diff) + 240) % 360

4. Saturation computation :

* if cmax = 0, then s = 0
* if cmax does not equal 0 then compute s = (diff/cmax)\*100

5. Value computation

* v = cmax\*100
