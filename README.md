# llama3-8b-alpaca-finetune
Llama 3 (8B) finetuned on [Alpaca instruction-tuning dataset generated with GPT4](https://huggingface.co/datasets/vicgalle/alpaca-gpt4)

### Training run details

This is the training run on Weights and Biases:
<img width="1364" alt="image" src="https://github.com/kevin-v96/llama3-8b-alpaca-finetune/assets/11131188/5f5ad090-5f6e-42e4-b0ba-ca0594e7fa84">

Here is the instruction template https://github.com/meta-llama/llama3?tab=readme-ov-file#instruction-tuned-models
Quoting below

The prompt begins with a <|begin_of_text|> special token, after which one or more messages follow. Each message starts with the <|start_header_id|> tag, the role system, user or assistant, and the <|end_header_id|> tag. After a double newline \n\n the contents of the message follow. The end of each message is marked by the <|eot_id|> token.

`<|begin_of_text|><|start_header_id|>system<|end_header_id|>

{{ system_prompt }}<|eot_id|><|start_header_id|>user<|end_header_id|>

{{ user_msg_1 }}<|eot_id|><|start_header_id|>assistant<|end_header_id|>

{{ model_answer_1 }}<|eot_id|>`

### Evaluation Details
Evaluated using AutoEval: https://github.com/mlabonne/llm-autoeval

### Evaluation Scores
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


|                                          Model                                          |AGIEval|GPT4All|TruthfulQA|Bigbench|Average|
|-----------------------------------------------------------------------------------------|------:|------:|---------:|-------:|------:|
|[llama3-8b-alpaca-lora-peft](https://huggingface.co/MadMarx37/llama3-8b-alpaca-lora-peft)|     32|  70.82|     59.54|   37.32|  49.92|

### AGIEval
|             Task             |Version| Metric |Value|   |Stderr|
|------------------------------|------:|--------|----:|---|-----:|
|agieval_aqua_rat              |      0|acc     |19.69|±  |  2.50|
|                              |       |acc_norm|21.65|±  |  2.59|
|agieval_logiqa_en             |      0|acc     |32.87|±  |  1.84|
|                              |       |acc_norm|32.26|±  |  1.83|
|agieval_lsat_ar               |      0|acc     |19.13|±  |  2.60|
|                              |       |acc_norm|18.26|±  |  2.55|
|agieval_lsat_lr               |      0|acc     |32.35|±  |  2.07|
|                              |       |acc_norm|30.39|±  |  2.04|
|agieval_lsat_rc               |      0|acc     |49.07|±  |  3.05|
|                              |       |acc_norm|39.41|±  |  2.98|
|agieval_sat_en                |      0|acc     |54.85|±  |  3.48|
|                              |       |acc_norm|47.57|±  |  3.49|
|agieval_sat_en_without_passage|      0|acc     |35.44|±  |  3.34|
|                              |       |acc_norm|30.10|±  |  3.20|
|agieval_sat_math              |      0|acc     |39.09|±  |  3.30|
|                              |       |acc_norm|36.36|±  |  3.25|

Average: 32.0%

### GPT4All
|    Task     |Version| Metric |Value|   |Stderr|
|-------------|------:|--------|----:|---|-----:|
|arc_challenge|      0|acc     |53.67|±  |  1.46|
|             |       |acc_norm|54.78|±  |  1.45|
|arc_easy     |      0|acc     |81.14|±  |  0.80|
|             |       |acc_norm|77.65|±  |  0.85|
|boolq        |      1|acc     |80.67|±  |  0.69|
|hellaswag    |      0|acc     |60.96|±  |  0.49|
|             |       |acc_norm|79.50|±  |  0.40|
|openbookqa   |      0|acc     |37.80|±  |  2.17|
|             |       |acc_norm|47.00|±  |  2.23|
|piqa         |      0|acc     |81.18|±  |  0.91|
|             |       |acc_norm|81.18|±  |  0.91|
|winogrande   |      0|acc     |74.98|±  |  1.22|

Average: 70.82%

### TruthfulQA
|    Task     |Version|Metric|Value|   |Stderr|
|-------------|------:|------|----:|---|-----:|
|truthfulqa_mc|      1|mc1   |41.86|±  |  1.73|
|             |       |mc2   |59.54|±  |  1.50|

Average: 59.54%

### Bigbench
|                      Task                      |Version|       Metric        |Value|   |Stderr|
|------------------------------------------------|------:|---------------------|----:|---|-----:|
|bigbench_causal_judgement                       |      0|multiple_choice_grade|58.95|±  |  3.58|
|bigbench_date_understanding                     |      0|multiple_choice_grade|67.21|±  |  2.45|
|bigbench_disambiguation_qa                      |      0|multiple_choice_grade|31.01|±  |  2.89|
|bigbench_geometric_shapes                       |      0|multiple_choice_grade|21.73|±  |  2.18|
|                                                |       |exact_str_match      | 0.00|±  |  0.00|
|bigbench_logical_deduction_five_objects         |      0|multiple_choice_grade|25.20|±  |  1.94|
|bigbench_logical_deduction_seven_objects        |      0|multiple_choice_grade|18.57|±  |  1.47|
|bigbench_logical_deduction_three_objects        |      0|multiple_choice_grade|42.33|±  |  2.86|
|bigbench_movie_recommendation                   |      0|multiple_choice_grade|26.40|±  |  1.97|
|bigbench_navigate                               |      0|multiple_choice_grade|50.00|±  |  1.58|
|bigbench_reasoning_about_colored_objects        |      0|multiple_choice_grade|59.10|±  |  1.10|
|bigbench_ruin_names                             |      0|multiple_choice_grade|24.33|±  |  2.03|
|bigbench_salient_translation_error_detection    |      0|multiple_choice_grade|29.06|±  |  1.44|
|bigbench_snarks                                 |      0|multiple_choice_grade|46.96|±  |  3.72|
|bigbench_sports_understanding                   |      0|multiple_choice_grade|64.20|±  |  1.53|
|bigbench_temporal_sequences                     |      0|multiple_choice_grade|27.00|±  |  1.40|
|bigbench_tracking_shuffled_objects_five_objects |      0|multiple_choice_grade|21.60|±  |  1.16|
|bigbench_tracking_shuffled_objects_seven_objects|      0|multiple_choice_grade|15.83|±  |  0.87|
|bigbench_tracking_shuffled_objects_three_objects|      0|multiple_choice_grade|42.33|±  |  2.86|


Average: 37.32%

Average score: 49.92%

Elapsed time: 02:23:00
