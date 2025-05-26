# K-means ++

1. <mark style="color:purple;background-color:purple;">**Randomly take a data point as the 1st centroid - C1**</mark>
2. <mark style="color:purple;background-color:purple;">**Calculate the distance of each data point to this centroid - d1, d2....**</mark>
3. <mark style="color:purple;background-color:purple;">**Take sum of the square of the distance (d)**</mark>
4. <mark style="color:purple;background-color:purple;">**Divide d1,d2... by d**</mark>
5. <mark style="color:purple;background-color:purple;">**This will give us the probability for the next centroid**</mark>
6. <mark style="color:purple;background-color:purple;">**Select the point having highest probability as centroid - C2**</mark>
7. <mark style="color:purple;background-color:purple;">**Now again for each point find distance to C1 and C2**</mark>
8. <mark style="color:purple;background-color:purple;">**For each point find the distance to the closest centroid - d1, d2...**</mark>
9. <mark style="color:purple;background-color:purple;">**Repeat steps 3 to 6 to get the next centroid**</mark>
