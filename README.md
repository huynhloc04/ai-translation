# AI Agent Translation

## 1. Features

- Change the tone (translation results) based on the provided context to match with desired.
- Give feedbacks to the previous translation to improve the result according to
  user's means.
- Support target languages: English, Spanish, Chinese, German, French, Italian

## 2. What makes this superior compared to others

- Leverage LLMs-based knowledge to get the best results
- Different contexts will give different translation results based on the context provided.
- Users can give feedbacks for better translation results

## 3. Tech stacks
FastAPI, PostgreSQL, Docker, AWS EC2, DeepL, Langchain, OpenAI, Mistral model, Ngrok, Git, ...

## 4. Run the app

- Give your original text and the desired target language type as the following:

```bash
{
    "text": "Tôi đi học.",
    "target_lang": "EN-US"
}
```

With an simple example above. I give the original text in Vietnamese and the target is English"

Run the API and we get the translated result looks like (in the "translated_text" field):

```bash
{
  "question_id": 1,
  "translated_text": "I go to school."
}
```

The return has a field called "question_id". If we want to put "context" or "feedback" and refine the previous translation result, you can pass these field like this (don't forget to put "question_id" param so that the BOT can know your specific question):

### - First context: WhThis can be used to emphasize the fact that you do attend school, perhaps in response to a doubt or a statement implying otherwise.

```bash

{
    "question_id": 1,
    "text": "Tôi đi học.",
    "target_lang": "EN-US",
    "context": "Khi nhấn mạnh sự thật về việc đi học."
}
```

And here is your result:

```bash
{
  "question_id": 1,
  "translated_text": "I do go to school."
}
```

### - Second context: When explaining to someone that you are heading to school at the moment, possibly in response to a question about your current activities.

```bash

{
    "question_id": 1,
    "text": "Tôi đi học.",
    "target_lang": "EN-US",
    "context": "Khi giải thích với ai đó rằng bạn hiện đang đi học, có thể là để trả lời câu hỏi về các hoạt động hiện tại của bạn."
}
```

And here is your result:

```bash
{
  "question_id": 1,
  "translated_text": "I am currently studying.!"
}
```

### - You can give your feedback.

```bash
{
    "question_id": 1,
    "text": "Tôi đi học.",
    "target_lang": "EN-US",
    "context": "Khi giải thích với ai đó rằng bạn hiện đang đi học, có thể là để trả lời câu hỏi về các hoạt động hiện tại của bạn.",
    "feedback": "Tôi muốn câu trả lời phải dài dòng và chi tiết hơn, ví dụ như học về cái gì, ở đâu."
}
```

And the result is:

```bash
{
  "question_id": 1,
  "translated_text": "I am currently attending school, studying various subjects important for my education.",
}
```
