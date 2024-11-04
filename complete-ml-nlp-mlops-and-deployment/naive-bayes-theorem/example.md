# Example

| Outlook  | Temp | Humidity | Windy | Play Golf |
| -------- | ---- | -------- | ----- | --------- |
| Rainy    | Hot  | High     | True  | No        |
| Rainy    | Hot  | High     | True  | No        |
| Overcast | Mild | High     | True  | No        |
| Sunny    | Cool | Low      | False | Yes       |
| Sunny    | Cool | Low      | False | Yes       |
| Sunny    | Hot  | Normal   | True  | Yes       |
| Overcast | Mild | Normal   | False | Yes       |
| Rainy    | Cool | High     | False | Yes       |
| Rainy    | Hot  | Low      | True  | No        |

* Probability of playing golf when outlook, temp, humidity, windy has already occurred independently

| Play Golf |   |              |
| --------- | - | ------------ |
| Yes       | 5 | P(Yes) = 5/9 |
| No        | 4 | P(No)  = 4/9 |
|           | 9 |              |

&#x20;             &#x20;

| Outlook  | Played | Not played | P(Yes)                                          | P(No) |
| -------- | ------ | ---------- | ----------------------------------------------- | ----- |
| Rainy    | 1      | 3          | <p>It is rainy and we played golf</p><p>1/5</p> | ¾     |
| Overcast | 1      | 1          | 1/5                                             | 1/4   |
| Sunny    | 3      | 0          | 3/5                                             | 0     |
|          | 5      | 4          |                                                 |       |

&#x20;              &#x20;

| Temp | Played | Not played | P(Yes)                                        | P(No) |
| ---- | ------ | ---------- | --------------------------------------------- | ----- |
| Hot  | 1      | 3          | <p>It is hot and we played golf</p><p>1/5</p> | ¾     |
| Cool | 3      | 0          | 3/5                                           | 0     |
| Mild | 1      | 1          | 1/5                                           | 1/4   |
|      | 5      | 4          |                                               |       |

&#x20;

| Humidity | Played | Not played | P(Yes)                                         | P(No) |
| -------- | ------ | ---------- | ---------------------------------------------- | ----- |
| High     | 1      | 3          | <p>It is high and we played golf</p><p>1/5</p> | ¾     |
| Low      | 2      | 1          | 2/5                                            | ¼     |
| Normal   | 2      | 0          | 2/5                                            | 0     |
|          | 5      | 4          |                                                |       |

&#x20;

| Windy | Played | Not played | P(Yes)                                        | P(No) |
| ----- | ------ | ---------- | --------------------------------------------- | ----- |
| True  | 1      | 4          | <p>It is hot and we played golf</p><p>1/5</p> | 4/4   |
| False | 4      | 0          | 4/5                                           | 0/4   |
|       | 5      | 4          |                                               |       |

&#x20;

* New data 🡪 Sunny, Cool, High, False 🡪 P(Yes) ??
* P(Yes | Sunny, Cool, High, False)
* P(No  | Sunny, Cool,  High, False)
* P(Yes|Sunny, Cool. High, False) = P(Sunny|Y) .P(Cool|Y).P(High|Y).P(False|Y).P(Y) / P(S,C,H,F)
* \= 3/5. 3/5.1/5.4/5.5/9 = 0.032
* P(N|S,C,H,F) = 0.
