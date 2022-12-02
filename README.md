# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил:
- Безбородов Вениамин Васильевич
- РИ210940
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 80 |
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
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Измените параметры файла. yaml-агента и определить какие параметры и
как влияют на обучение модели.

Чкачал и запустил проект, установил ml-agents-19.
![Screenshot_1](https://user-images.githubusercontent.com/49115035/205266028-eebb7d35-5227-486a-99ee-c39c43ff27f9.png)


конфигурационный файл Economic.yaml
```yaml
  behaviors:
  Economic:
    trainer_type: ppo
    hyperparameters:
      batch_size: 1024
      buffer_size: 10240
      learning_rate: 3.0e-4
      learning_rate_schedule: linear
      beta: 1.0e-2
      epsilon: 0.2
      lambd: 0.95
      num_epoch: 3      
    network_settings:
      normalize: false
      hidden_units: 128
      num_layers: 2
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 1.0
    checkpoint_interval: 500000
    max_steps: 750000
    time_horizon: 64
    summary_freq: 5000
    self_play:
      save_steps: 20000
      team_change: 100000
      swap_steps: 10000
      play_against_latest_model_ratio: 0.5
      window: 10
```

Скачал torch и mlagent, запустил обучение в консоли увидел считывание файла
![Screenshot_2](https://user-images.githubusercontent.com/49115035/205266649-792d4fe0-3c27-4141-b9c6-6dfeba3a51d7.png)

После обучения запустил tensorboard
![Screenshot_3](https://user-images.githubusercontent.com/49115035/205269251-214dd1dd-d43f-4ac1-948b-5904fa06955e.png)

Начал редактирование Economic.yaml файла 5 раз.

1. Изменил ```batch_size: 1024``` на  ```batch_size: 2500``` 
![Screenshot_4](https://user-images.githubusercontent.com/49115035/205270647-dadb5159-2415-4f13-96e5-33c5e868fa68.png)
Из-за этого график стал прямым и равнялся единице.

2. После этого сменил ```batch_size: 2500``` на ```batch_size: 512``` 
![Screenshot_5](https://user-images.githubusercontent.com/49115035/205272134-803013d9-d440-4db6-acab-34825cf2ae7f.png)
график перестал быть прямым и стал возрастающим

3. После этого осатвил прошлые настройки и сменил ```lambd: 0.95``` на ```lambd: 0.85```
![Screenshot_6](https://user-images.githubusercontent.com/49115035/205274474-18012a09-96c7-4c51-8786-157800ea786d.png)
График почти не изменился, но стал чуть более изогнутым

4. После этого сменил ```num_epoch: 3``` на ```num_epoch: 1```
![Screenshot_7](https://user-images.githubusercontent.com/49115035/205276334-aade0aaa-8035-4aeb-9804-6c84fe822369.png)

Это оказалось плохой идеей, и график пошел вниз из-за нехватки эпох

5.Затем верунл ```num_epoch: 3``` и поменял ```epsilon: 0.2``` на ```epsilon: 0.1```
![Screenshot_8](https://user-images.githubusercontent.com/49115035/205277720-e998002c-4bf7-4974-a86c-3de713f7bbcd.png)
График упал, но затем начал расти обратно


## Задание 2
### Сделать подгрузку результатов 1 лабы в гугл таблицы.

## Выводы
Я научился подгружать и загружать данные из гугл таблиц при помощи связки python , C#


