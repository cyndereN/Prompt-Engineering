# ChatGPT Prompt Engineering for Developers

## 1. Introduction

### 1.1 Two Types of Large Language Models (LLMs)

- Base LLM

    Predicts next word, based on text training data.

- Intstruction Tuned LLM

    Tries to follow instructions. Fine-tune on instructions and good attempts at following those instructions

    RLHF (Reinforcement Learning with Human Feedback)

    Helpful, Honest, Harmless.

## 2. Guidelines

### 2.1 Principle 1: Write clear and specific instructions



#### 2.1.1 Tactic 1: Use delimiters to clearly indicate distinct parts of the input

#### 2.1.2 Tactic 2: Ask for a structured output

#### 2.1.3 Tactic 3: Ask the model to check whether conditions are satisfied

```python
text_1 = f"""
Making a cup of tea is easy! First, you need to get some \ 
water boiling. While that's happening, \ 
grab a cup and put a tea bag in it. Once the water is \ 
hot enough, just pour it over the tea bag. \ 
Let it sit for a bit so the tea can steep. After a \ 
few minutes, take out the tea bag. If you \ 
like, you can add some sugar or milk to taste. \ 
And that's it! You've got yourself a delicious \ 
cup of tea to enjoy.
"""
prompt = f"""
You will be provided with text delimited by triple quotes. 
If it contains a sequence of instructions, \ 
re-write those instructions in the following format:

Step 1 - ...
Step 2 - …
…
Step N - …

If the text does not contain a sequence of instructions, \ 
then simply write \"No steps provided.\"

\"\"\"{text_1}\"\"\"
"""
response = get_completion(prompt)
print("Completion for Text 1:")
print(response)
```
#### 2.1.4 Tactic 4: "Few-shot" prompting

"example"

```python
prompt = f"""
Your task is to answer in a consistent style.

<child>: Teach me about patience.

<grandparent>: The river that carves the deepest \ 
valley flows from a modest spring; the \ 
grandest symphony originates from a single note; \ 
the most intricate tapestry begins with a solitary thread.

<child>: Teach me about resilience.
"""
response = get_completion(prompt)
print(response)
```

### 2.2 Principle 2: Give the model time to “think”

#### 2.2.1 Tactic 1: Specify the steps required to complete a task

#### 2.2.2 Tactic 2: Instruct the model to work out its own solution before rushing to a conclusion

### 2.3 Model Limitations: Hallucinations

幻觉 (hallucination) / plausible (貌似真实的 似是而非的)

Make statements that sound plausible but are not true

## 3. Iterative

### 3.1 Issue 1: The text is too long

Limit the number of words/sentences/characters.

### 3.2 Issue 2. Text focuses on the wrong details

Ask it to focus on the aspects that are relevant to the intended audience.

### 3.3 Issue 3. Description needs a table of dimensions

Ask it to extract information and organize it in a table.

## 4. Summarizing

- with a word/sentence/character limit 
- with a focus
- Try "extract" instead of "summarize"

## 5. Inferring

- Sentiment (positive/negative)
- Identify types of emotions
- Extract product and company name from customer reviews
- Inferring topics