# UPDATE 18.05.2022
- Веса модели для детекции штрихкодов (нотбук `barcode-project-det.ipynb`) можно найти [здесь](https://drive.google.com/file/d/14A524MVX0Fg_HvQ1Ee4zL_MXOvPphRQm/view?usp=sharing).
- Веса модели распознавания штрихкодов (ноутбуки `barcode-project-rec-training.ipynb` и `barcode-project-rec-inference-final.ipynb`) доступны по [этой ссылке](https://drive.google.com/file/d/1cHhLdfMqGAxgvUBbH0Wad3yreNJ8l22V/view?usp=sharing).
- Ноутбук `barcode-project-rec-inference-final.ipynb` включает в себя как часть с обучением рекогнайзера, так и часть с инференсом, где используются сразу обе модели: детектор и рекогнайзер (см. секцию **Submit result** в конце ноутбука).

# Задание 3: распознавание штрихкодов

## Описание
На изображениях находятся штрихкоды EAN13. На каждом изображении есть только один штрихкод.

Подробная спецификация: http://www.gomaro.ch/Specifications/EAN13e.htm

Требуется локализовать баркод и распознать.
**Можно обучить нейросетевую модель или реализовать эвристическое решение.**  (изменено 11.05)

**Библиотеки для работы с изображениями использовать можно, но ЗАПРЕЩЕНО использовать готовые решения, которые самостоятельно находят или распознают штрихкоды! 
При использовании готового решения - соответствующая метрика обнуляется.** (изменено 11.05)

## Данные
Все данные можно найти здесь:

https://drive.google.com/drive/folders/1HMWgyJS0dH2XpGqMhfN8kYGMziBqKe5v

Train - директория с данными для обучения:

- В папке Images находятся изображения.

- markup.csv - разметка всех изображений.

- markup_wo_inverted.csv - разметка всех изображений, кроме выворотки (напечатанные белым на черном).

- Разметка представляет собой csv файл следующего формата:
{имя файла},{значение штрихкоды},{координаты объекта - 4 пары x1, y1, x2, y2, x3, y3, x4, y4},{разметка модулей штрихкода, 1-черный модуль, 0-белый модуль}.


Train/Inverted - директория с данными с вывороткой:

- Images - изображения с вывороткой.

- markup.csv - разметка таких изображений.


Test/Images - директория с изображениями контрольной выборки.

В качестве распознанного текста нужно получить ответ из 13 цифр.

В качестве локализованного баркода нужно получить 4 пары x1, y1, x2, y2, x3, y3, x4, y4 - координаты углов четырехугольника. 


answer.csv - пример ответа

markup.csv - ground truth разметка изображений из Test


## Оценка
Чтобы решение было зачтено, весь код (модели, скрипты, ноутбуки) для воспроизведения ваших результатов должен быть в вашем репозитории.

Результат считается на выборке из папки Test.


Баркод считается распознанным верно, если закодированный текст полностью совпал с результатом.

Итоговое количество баллов за задание = (0.65 * #{Доля верно распознанных баркодов} + 0.35 * #{Доля примеров с IoU > 0.5}) * 100


## Дедлайн
18 мая 2022 включительно
