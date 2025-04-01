# Large Reasoning Models

* Vanilla Transformers alone are not sufficient for complex reasoning
* Chain-of-Thought prompting explicitly encourages the model to generate intermediate  \
  reasoning steps before arriving at a final answer
* Tree-of-Thoughts takes this  &#x20;further, exploring multiple reasoning paths and using a search algorithm to find the most  &#x20;promising solution
* Fine-tuning on datasets specifically designed for reasoning tasks is also crucial.&#x20;
* These  &#x20;datasets may contain logical puzzles, mathematical problems, or commonsense reasoning  \
  challenges.&#x20;
* Instruction tuning, where the model is trained to follow natural language  &#x20;instructions, further enhances its ability to understand and respond to complex reasoning  &#x20;prompts.&#x20;
* Reinforcement Learning from Human Feedback (RLHF) refines the model’s outputs  \
  based on human preferences, improving the quality and coherence of its reasoning.
* Knowledge distillation, transferring knowledge from a larger, more capable “teacher” model  \
  to a smaller, more efficient “student” model, can be used to improve the reasoning abilities  \
  of smaller models while maintaining efficiency.&#x20;
* This approach allows the student model to  &#x20;learn the reasoning patterns of the teacher model without requiring the same computational  \
  resources.
