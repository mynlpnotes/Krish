# Principles for Prompting

**Principles:**

1. Write clear and specific instructions
   1. Use delimiters
      1. """"     \`\`\`     -—  <>   \<xml tags>
      2. Any clear punctuation that separates text from prompt
      3. It also helps avoid prompt injection
      4.

          <figure><img src="../../.gitbook/assets/{8849ED12-9308-4ED1-92EA-4E633A7583D1}.png" alt=""><figcaption></figcaption></figure>


   2. Ask for structured output:
   3. Check whether conditions are satisfied
      1. Check assumptions required to do the task
   4.  Few-shot programming

       1. Give successful examples of completing tasks, then ask model to perform the task


2. Give model time to think
   1. Specify the steps required to compete the task
   2. Instruct the model to work out its own solution before rushing to an conclusion

* If the model is making reasoning errors, rushing to an incorrect conclusion, then we can try reframing query to request a chain or series of relevant reasoning
* If model is given complex task, then it make a guess which may be incorrect, so there we can ask model to think longer





We will be using openai library

