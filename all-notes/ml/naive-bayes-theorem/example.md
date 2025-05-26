---
hidden: true
---

# Example

**Training Data**

| Email | Word: "buy" | Word: "cheap" | Word: "money" | Label    |
| ----- | ----------- | ------------- | ------------- | -------- |
| 1     | Yes         | Yes           | No            | Spam     |
| 2     | No          | Yes           | Yes           | Spam     |
| 3     | Yes         | No            | No            | Not Spam |
| 4     | No          | No            | Yes           | Not Spam |
| 5     | Yes         | Yes           | Yes           | Spam     |
| 6     | Yes         | No            | Yes           | Not Spam |
| 7     | No          | Yes           | No            | Spam     |

**New Email**

* **"buy: Yes"**, **"cheap: Yes"**, **"money: No"**

***

**Step 1: Calculate Prior Probabilities**

| Class    | Formula                                        | Calculation | Result |
| -------- | ---------------------------------------------- | ----------- | ------ |
| Spam     | P(Spam) = (# of Spam) / (Total emails)         | 4/7         | 0.571  |
| Not Spam | P(Not Spam) = (# of Not Spam) / (Total emails) | 3/7         | 0.429  |

***

**Step 2: Calculate Likelihoods**

<table><thead><tr><th>Word Condition</th><th>Class</th><th>Result</th><th data-hidden>Formula</th><th data-hidden>Calculation</th></tr></thead><tbody><tr><td>buy = Yes</td><td>Spam</td><td>2/4</td><td>P(buy = Yes</td><td>Spam)</td></tr><tr><td>cheap = Yes</td><td>Spam</td><td>3/4</td><td>P(cheap = Yes</td><td>Spam)</td></tr><tr><td>money = No</td><td>Spam</td><td>2/4</td><td>P(money = No</td><td>Spam)</td></tr><tr><td>buy = Yes</td><td>Not Spam</td><td>2/3</td><td>P(buy = Yes</td><td>Not Spam)</td></tr><tr><td>cheap = Yes</td><td>Not Spam</td><td>0/3</td><td>P(cheap = Yes</td><td>Not Spam)</td></tr><tr><td>money = No</td><td>Not Spam</td><td>1/3</td><td>P(money = No</td><td>Not Spam)</td></tr></tbody></table>

***

**Step 3: Apply Naive Bayes Formula for Each Class**

**1. Calculate ( P(\text{Spam | Data}) ):**

| Class | Formula        | Calculation                | Result                    |
| ----- | -------------- | -------------------------- | ------------------------- |
| Spam  | ( P(\text{Spam | Data}) \propto P(buy = Yes | Spam) \cdot P(cheap = Yes |

**2. Calculate ( P(\text{Not Spam | Data}) ):**

| Class    | Formula            | Calculation                | Result                        |
| -------- | ------------------ | -------------------------- | ----------------------------- |
| Not Spam | ( P(\text{Not Spam | Data}) \propto P(buy = Yes | Not Spam) \cdot P(cheap = Yes |

***

**Step 4: Final Decision**

| Class    | Probability (Proportional) | Result     |
| -------- | -------------------------- | ---------- |
| Spam     | 0.107                      | **Higher** |
| Not Spam | 0.0                        | Lower      |
