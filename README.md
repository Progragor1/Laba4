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

#### OR
![0](https://user-images.githubusercontent.com/91984484/202422116-a57c09df-4144-4a1c-bc2a-4059ae265984.jpg)

#### Перцептрон обучается быстро. За 4 эпохи корректность минимизирует ошибки до 0 и работает корректно.
#### AND
![1](https://user-images.githubusercontent.com/91984484/202422180-643ca7ed-c913-47f4-a70e-05c9911cd28d.jpg)

#### Перцептрон обучается дольше предыдущего, а именно за 8 эпох начинает работать корректно.
#### NAND
![2](https://user-images.githubusercontent.com/91984484/202422279-1e728cca-5cb6-4add-9b98-fcb7e6a0de85.jpg)

#### Перцептрон обучается также за 8 эпох, но на второй эпохе значение TOTAL ERROR достигает 3, после чего понижается до 0, и перцептрон работает корректно.
#### XOR
![3](https://user-images.githubusercontent.com/91984484/202422326-131e8ca1-a364-49d2-ba33-b5e7f793ec20.jpg)

#### Так как перцептрон работает только с линейно разделимыми объектами, он не способен решить данную логическую задачу, потому что для её решения потребуется разделить данные двумя линиями. Перцептрон на это не способен, и при повышении количества тренировок TOTAL ERROR становиться равным 4 и работает не корректно. 
## Задание 2
### Подробно опишите каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта по ссылке. Самостоятельно найдите информацию о компонентах Decision Requester, Behavior Parameters, добавленных на сфере.
```py
// Подключаем необходимые библиотеки
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody; // создаем переменную типа Rigitbody
    void Start()
    {
        rBody = GetComponent<Rigidbody>();  // присваеваем значение фактического компонента, обеспечивающего физическое взаимодействие между объектами
    // Start вызывается перед первым обновлением кадра
    }

    public Transform Target; // создаем объект куб
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0) // если координата y объекта меньше 0, то
        {
            this.rBody.angularVelocity = Vector3.zero; //задаем скорость поворота
            this.rBody.velocity = Vector3.zero; // задаем направление движения тела
            this.transform.localPosition = new Vector3(0, 0.5f, 0); // задаем координаты объекта
        }

        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);// перемещаем объект в случайное место
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition); //добавляет в вектор наблюдения положение объекта
        sensor.AddObservation(this.transform.localPosition); // добавляет в вектор наблюдения положение перемещенного объекта
        sensor.AddObservation(rBody.velocity.x); // добавляет в вектор наблюдения координату x
        sensor.AddObservation(rBody.velocity.z); // добавляет в вектор наблюдения координату y
    }
    public float forceMultiplier = 10; // создаем множитель силы
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero; // направление силы
        controlSignal.x = actionBuffers.ContinuousActions[0]; // начало непрерывных действий по координате x
        controlSignal.z = actionBuffers.ContinuousActions[1]; // начало непрерывных действий по координате y
        rBody.AddForce(controlSignal * forceMultiplier); // примененяем физическую силу к объекту

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition); // расстояние до куба

        if(distanceToTarget < 1.42f) // если дистанция до объекта меньше 1.42, то
        {
            SetReward(1.0f); // изменяем вознаграждение за эпизод 
            EndEpisode(); // заканчиваем эпизод
        }
        else if (this.transform.localPosition.y < 0)// если координата y объекта меньше 0, то
        {
            EndEpisode(); // заканчиваем эпизод
        }
    }
}

```

## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и в первом задании, случайно изменять координаты на плоскости. В выводах к работе дайте развернутый ответ, что такое игровой баланс и как системы машинного обучения могут быть использованы для того, чтобы его скорректировать.


## Выводы
### В результате работы:
#### - Реализовал систему машиного обучения в связке Python - Google-Sheets - Unity.
#### - Посмотрел, как обучается модель
#### - Проанализировал программный код, который способствовал обучению модели
#### - Изучил информацию о компонентах Decision Requester, Behavior Parameters



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
