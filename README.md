# llama3-8b-alpaca-finetune
Llama 3 (8B) finetuned on Alpaca instruction-tuning dataset generated with GPT4

<img width="1364" alt="image" src="https://github.com/kevin-v96/llama3-8b-alpaca-finetune/assets/11131188/5f5ad090-5f6e-42e4-b0ba-ca0594e7fa84">

Evaluated using AutoEval: https://github.com/mlabonne/llm-autoeval

This is currently Meta-Llama3-8B on [eqbench](https://eqbench.com/):
<img width="1306" alt="image" src="https://github.com/kevin-v96/llama3-8b-alpaca-finetune/assets/11131188/87d8393f-77e7-45b6-ac45-18ae812beda0">

|                                          Model                                          |EQ-Bench|Average|
|-----------------------------------------------------------------------------------------|-------:|------:|
|[llama3-8b-alpaca-lora-peft](https://huggingface.co/MadMarx37/llama3-8b-alpaca-lora-peft)|   29.42|  29.42|

### EQ-Bench
|  Task  |Version|           Metric            | Value  |   |Stderr|
|--------|------:|-----------------------------|--------|---|------|
|eq_bench|    2.1|eqbench,none                 |   29.42|   |      |
|        |       |eqbench_stderr,none          |    3.58|   |      |
|        |       |percent_parseable,none       |     100|   |      |
|        |       |percent_parseable_stderr,none|       0|   |      |
|        |       |alias                        |eq_bench|   |      |

Average: 29.42%

Average score: 29.42%

Elapsed time: 00:12:31
