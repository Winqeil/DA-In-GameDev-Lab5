# Интеграция экономической системы в проект Unity и обучение ML-Agent
Отчет по лабораторной работе #5 выполнил(а):
- Намесников Глеб Артёмович
- РИ210912
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с работой ML Агента в экономической системе с помощью TensorBoard.

## Задание 1
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
Ход работы:

- Были успешно установлены необходимые пакеты (ML Agents, PyTorch) для запуска обучения. ![image](https://user-images.githubusercontent.com/103383207/205135414-e44c586c-a8ed-4722-9f97-0c4b9736128e.png)

- Был добавлен Economic.yaml файл с содержанием ниже.

```cs

default_settings: null
behaviors:
  Economic:
    trainer_type: ppo
    hyperparameters:
      batch_size: 1024
      buffer_size: 10240
      learning_rate: 0.0003
      beta: 0.01
      epsilon: 0.2
      lambd: 0.95
      num_epoch: 3
      learning_rate_schedule: linear
      beta_schedule: linear
      epsilon_schedule: linear
    network_settings:
      normalize: false
      hidden_units: 128
      num_layers: 2
      vis_encode_type: simple
      memory: null
      goal_conditioning_type: hyper
      deterministic: false
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 1.0
        network_settings:
          normalize: false
          hidden_units: 128
          num_layers: 2
          vis_encode_type: simple
          memory: null
          goal_conditioning_type: hyper
          deterministic: false
    init_path: null
    keep_checkpoints: 5
    checkpoint_interval: 500000
    max_steps: 750000
    time_horizon: 64
    summary_freq: 5000
    threaded: false
    self_play:
      save_steps: 20000
      team_change: 100000
      swap_steps: 10000
      window: 10
      play_against_latest_model_ratio: 0.5
      initial_elo: 1200.0
    behavioral_cloning: null
env_settings:
  env_path: null
  env_args: null
  base_port: 5005
  num_envs: 1
  num_areas: 1
  seed: -1
  max_lifetime_restarts: 10
  restarts_rate_limit_n: 1
  restarts_rate_limit_period_s: 60
engine_settings:
  width: 84
  height: 84
  quality_level: 5
  time_scale: 20
  target_frame_rate: -1
  capture_frame_rate: 60
  no_graphics: false
environment_parameters: null
checkpoint_settings:
  run_id: Economic
  initialize_from: null
  load_model: false
  resume: false
  force: true
  train_model: false
  inference: false
  results_dir: results
torch_settings:
  device: null
debug: false

```

- Для оценки обучения был установлен TensorBoard. ![image](https://user-images.githubusercontent.com/103383207/205135789-f07976ac-70be-4740-aa9f-fce342b90c47.png)

- Далее были изменены параметры yaml файла (batch_size, num_epoch, epsilon, lambd) для оценки изменений Cumulative Reward.

batch_size = 3000. График ведет себя более линейно, однако Value Loss стремится не к нулю, а вверх. ![image](https://user-images.githubusercontent.com/103383207/205136250-4ec5faa5-be62-43c0-8d47-8c60c04522cc.png)

batch_size = 250 ![image](https://user-images.githubusercontent.com/103383207/205136568-003f495d-f67c-492d-94be-7042a24e5ba6.png)

lambd = 0.8. Никаких изменений в графике. ![image](https://user-images.githubusercontent.com/103383207/205136925-6b596a2a-4674-4514-a924-1db400641b71.png)

epsilon = 0.1. Менее линейный график с резким скачком. ![image](https://user-images.githubusercontent.com/103383207/205137095-c1fbb9b5-9c18-4bf6-8f3f-6e57b4de4bfe.png)

num_epoch = 2. График стал наиболее линейным. ![image](https://user-images.githubusercontent.com/103383207/205137248-b18470e6-0b67-4567-a612-41fc345b3304.png)

## Задание 2
### 


## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
