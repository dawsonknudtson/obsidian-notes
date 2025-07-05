source : [[google-prompt-engineering.pdf]]

--------------------------------------------------------------

**Output Config** :

Effective prompt engineering requires setting these optimally for task, 

**Output Length** : 

- Tokens to generate in a response 
- Tokens Obviously require more computation for the LLM
- Output Restriction is important for some LLM prompting techniques
	- Like ReAct, where the LLM will keep emitting tokens after the response you want 


Token Definition : Unit of Text that the model breaks down, aka tokenization 

**Sampling Control** :

- LLM's predict probabilities for what the next token could be, each token in the LLM's vocab getting a probability
- Tokens are sampled to determine what the next produced token will be
- Temperature, top-K and top-P, most common config settings that determine how predicted token probabilities are processed to choose a single output token 

[Sampling Control]
[Further Research Needed ]

**Temperature** :

Controls the degree of randomness in token selection, Low temp are good for prompts the expect a deterministic response, higher temps can lead to more diverse or unexpected results.

- Temp's closer to max tend to create a more random output
- Gemini Temp control can be understood in a similar way to the softmax function in ML


**Top-K and Top-P** :
(nucleus sampling)


	Top-K : Samping selects the top K most likely tokens from a model's predicted distribution. The higher top-K, the more creative and varied the model's output; the lower top-k, the more restive and factual the model's output
		- A top-K is equiv to greedy decoding 


	Top-P : Sampling selects the top tokens whose probability does not exceed a certain value(P). Values for P range from 0(greedy decoding) to 1 (all tokens in the LLM's vocab)

- Best way to choose between these two is to experiment with both and see which produces the results you are looking for 
- Another Important config is the number of tokens to generate in response
	- Generating more tokens require more computation from the LM, leading to higher energy consumption and potentially slower response times, which can cost more 



- General Starting point, a temp of .2, top-p of .95 and top-k of 30, will give relatively coherent results - can adjust to temp .1 - p .9 - k .20 for less creative results
- Single Correct answer's (math) - start w/ temp 0 


**Prompting Techniques** : 

[zero-shot]

Provide a description of task and some text for the LLM to get started. Input could be : questions, start of story, instructions.



| Name        | 1_1_movie glassification                                                                                                                                                                                                                                              |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Goal        | Classify movie reviews as positive, neutral or negative                                                                                                                                                                                                               |
| Model       | gemini-pro                                                                                                                                                                                                                                                            |
| Temperature | .1               \| Token Limit \|  5                                                                                                                                                                                                                                 |
| Top-K       | N/A           \| Top - P         \|  1                                                                                                                                                                                                                                |
| Prompt      | Classify movie reviews as POSITIVE, NEUTRAL or NEGATIVE.<br>Review : "Her" is a disturbing study revealing the direction humanity <br>is headed if AI is allowed to keep evolving, <br>unchecked. I wish there were more movies like this masterpiece.<br>Sentiment : |
| Output      | POSITIVE                                                                                                                                                                                                                                                              |


[one-shot]

A one-shot prompt, provides a single example, hence the name one-shot. The idea is the model has an example it can imitate to best complete the task.

[few-shot]

A few-shot prompt 7 provides multiple examples to the model. This approach shows the model a pattern that it needs to follow. The idea is similar to one-shot, but multiple examples of the desired pattern increases the chance the model follows the pattern.



| Goal        | Parse pizza orders to JSON                                                                                                                                                                                                                                                                                                          |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Model       | gemini-pro                                                                                                                                                                                                                                                                                                                          |
| Temperature | .1           \|   Token Limit   \| 250                                                                                                                                                                                                                                                                                              |
| Top-K       | N/A       \|    Top-P            \| 1                                                                                                                                                                                                                                                                                               |
| Prompt      | Parse a customer's pizza order into valid JSON: <br><br>EXAMPLE: I want a small pizza with cheese, tomato sauce, and pepperoni. JSON Response: ``` <br><br>{ "size": "small", <br>"type": "normal", "ingredients": [["cheese", "tomato sauce", "peperoni"]] <br>} ```                                                               |
| Prompt      | EXAMPLE: <br>Can I get a large pizza with tomato sauce, basil and mozzarella <br>{ <br>"size": "large", <br>"type": "normal", <br>"ingredients": tomato sauce, bazel, mozzarella} <br><br>Now, I would like a large pizza, with the first half cheese and mozzarella. And the other tomato sauce, ham and pineapple. JSON Response: |
| Output      | <br>{ <br>"size": "large", <br>"type": "half-half", <br>"ingredients": cheese, mozzarella, tomato sauce, ham, pineapple<br>}<br>                                                                                                                                                                                                    |

-  **System prompting** sets the overall context and purpose for the language model. It defines the ‘big picture’ of what the model should be doing, like translating a language, classifying a review etc.
- **Contextual prompting** provides specific details or background information relevant to the current conversation or task. It helps the model to understand the nuances of what’s being asked and tailor the response accordingly.
- **Role prompting** assigns a specific character or identity for the language model to adopt. This helps the model generate responses that are consistent with the assigned role and its associated knowledge and behavior. 



- System prompt: Defines the model’s fundamental capabilities and overarching purpose.
- Contextual prompt: Provides immediate, task-specific information to guide the response. It’s highly specific to the current task or input, which is dynamic.
- Role prompt: Frames the model’s output style and voice. It adds a layer of specificity and personality.

[ System Prompting ]

