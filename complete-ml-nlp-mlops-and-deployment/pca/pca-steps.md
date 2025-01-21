# PCA Steps

1. Take a dataset with mean as 0 and std dev as 1
   1. (X – mean)/std dev
   2. PCA does not work on normally distributed data, it needs standard normally distributed data
2. Draw a single line which is going to explain the data
   1. Find best fitted line 🡪 residuals should be as small as possible
3. If we project any point on this line, then that point represents both the coordinates x1 and x2
   1. x2 = mx1 +x
4. This straight line which we draw is knows as principal component 1
5. Principal component line is nothing but a line which is holding relation of all the other components
6. Now take PC1 and rotate it as a axis and along with it rotate all the data points as well
7. Now we draw a perpendicular line to the axis
8. To form a new coordinate system
9. We will take the perpendicular line as PC2
10. PC3 will be perpendicular to PC1 and PC2
