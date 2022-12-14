# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе №4 выполнил:
- Султанов Егор Альбертович
- РИ-210948

Отметка о выполнении заданий:

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


## Цель работы
Познакомиться с перцептроном и реализовать его обучение на Unity.
## Задание 1
### В проекте Unity реализовать перцептрон, который умеет производить вычисления.

### OR
![0](https://user-images.githubusercontent.com/91984484/202422116-a57c09df-4144-4a1c-bc2a-4059ae265984.jpg)
![1](https://user-images.githubusercontent.com/91984484/202422180-643ca7ed-c913-47f4-a70e-05c9911cd28d.jpg)

### Перцептрон обучается быстро. За 4 эпохи обучениия ошибки минимизируются до 0 и работает корректно.
### AND
![AND](https://user-images.githubusercontent.com/91984484/202424931-cb50f837-dda0-4b74-b7a6-3e59371e70be.jpg)

### Перцептрон обучается дольше предыдущего, а именно за 8 эпох начинает работать корректно.
### NAND
![2](https://user-images.githubusercontent.com/91984484/202422279-1e728cca-5cb6-4add-9b98-fcb7e6a0de85.jpg)

### Перцептрон обучается также за 8 эпох, но на второй эпохе значение TOTAL ERROR достигает 3, после чего понижается до 0, и перцептрон работает корректно.
### XOR
![3](https://user-images.githubusercontent.com/91984484/202422326-131e8ca1-a364-49d2-ba33-b5e7f793ec20.jpg)

### Так как перцептрон работает только с линейно разделимыми объектами, он не способен решить данную логическую задачу, потому что для её решения потребуется разделить данные двумя линиями. Перцептрон на это не способен, и при повышении количества тренировок TOTAL ERROR становиться равным 4 и работает не корректно. 
## Задание 2
### Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.
### OR
![Chart](https://user-images.githubusercontent.com/91984484/202425950-27acf2b8-dd5f-4ad2-940e-f58ec10f079e.jpg)
### AND 
![Chart (1)](https://user-images.githubusercontent.com/91984484/202425994-bdaded7e-ff84-4ef4-8f44-db710a41bd8b.jpg)
### NAND
![Chart (2)](https://user-images.githubusercontent.com/91984484/202426031-eaf7e228-08f5-43be-b6fa-0a8c39573fdb.jpg)
### XOR
![Chart (3)](https://user-images.githubusercontent.com/91984484/202426058-3515dba4-6127-4d5e-b96f-e38925382220.jpg)

### Количество эпох обучения зависит от
#### - Числа экземпляров в тренировочном наборе 
#### - Числа классов при решении задач классификации
#### - Коэффициента обучения(шаг обучения)
#### - Увеличения ошибки обобщения 
#### - Градиента функции-ошибки




## Выводы
### В результате работы:
#### - Познакомился с перцептроном
#### - Обучил перцептрон решать логические задачи
#### - Составил зависимость количества эпох от ошибки обучения
#### - Проанализировал от чего зависит количество эпох обучения



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
