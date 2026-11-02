# qualtrics-ai-responses

Real chatbot answers, rendered as images, for the Qualtrics survey "GenAI recommendations - Consumer Choice" (v8 and later).
The older placeholder images stay in [qualtrics-images](https://github.com/Saumyahbs/qualtrics-images), which is the test repo.

## What is here

```
ai_responses/
  manifest.json      read by the survey (products, prompts, models, third words for the Q26 check)
  manifest.csv       one row per image: product, model, tier, prompt, CSV idx and interaction_id, image URL
  intro_demo.gif     demo on the Image Intro page
  <category>/<product>/<model>__<prompt_type>.jpg
```

- **Answers:** from `df_clean_august.csv`, one per product, prompt type and model: the lowest `idx` with a non-blank answer.
- **Products:** the 99 survey products. "Car rental" has no real answers and was removed from the survey.
- **Prompt types:** `options` and `best` for every product, plus two of `features`, `use_case` and `max_price` for half of them.
- **Images:** answer text only, black on white, same layout for every model, no chatbot name. Shown at 390 px wide with 16 px text, saved at 2x.

## Models

Each participant is randomly shown one model set (saved as `ModelTier`); the model behind every image is saved as `Qk_L_Model` / `Qk_R_Model`.

| Chatbot  | top                    | fast               |
|----------|------------------------|--------------------|
| ChatGPT  | gpt-5.6-sol            | gpt-5.6-luna       |
| Gemini   | gemini-3.1-pro-preview | gemini-3.6-flash   |
| Claude   | claude-opus-5          | claude-sonnet-5    |
| DeepSeek | deepseek-v4-pro        | deepseek-v4-flash  |
| Grok     | grok-4.6               | grok-4.5           |
| Mistral  | mistral-medium-3.5     | mistral-medium-3.5 |

Image URL = `base_url` + model + `__` + prompt type + `.jpg`.
