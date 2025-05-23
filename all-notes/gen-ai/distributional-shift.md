---
hidden: true
---

# Distributional Shift

* The model then creates an expert policy, which acts like a rule book for how the model should respond to requests.&#x20;
* This policy is based on the conversations that SFT used to train the model.
* It only knows what it has taught, if we ask something else then it might give some random answer
* To keep this drift in check, the model needs to act proactively during the conversation and not passively answer what it has learned.
*   This is done using RLFH

    <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
*
