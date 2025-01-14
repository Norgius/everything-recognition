# Распознавание лиц
Данный проект позволяет в режиме реального времени распозновать лица и другие объекты в процессе съёмки.

## Порядок установки
Для работы вам потребуется `Python3` версии не ниже `3.6`.

Установите необходимые зависимости командой:
```
pip install -r requirements.txt
```

## Файл run.py
Основная логика проекта написана в данном файле. 

После запуска первое, что он делает - это считывание необходимых `каскадов` для захвата определенной области на картинке. `Каскады` берутся из папки `haarcascaded`. А вот какие конкретно берёт файл, будет объяснено позже.

Далее идёт подключение к `камере устройства`/`внешней камере`. Если такого устройства нет, то в терминале вы увидите:
```
Couldn't find your webcam... Sorry :c
```
и программа завершит работу.

Если всё успешно, файл начнёт покадрово считывать и обрабатывать видео.
Вся обработка проходит в сером цвете, так повышается точность нахождения нужных нам объектов.

К каждому видеокадру будут применятся по очереди `каскады`. И если нужный объект был найден, то он отрисовывается в виде прямоугольника определенным цветом. О том, какой цвет у каждого объекта, будет объяснено ниже.

Чтобы выйти из программы, необходимо нажать клавишу `q`. Окно с видеорядом закроется и программа завершит работу.

## Файл config.py
Содержит ссылки к выбранным `каскадам`. 
В нашем случае выбраны `каскады` типа:
* Лицо, вид спереди
* Лицо, вид сбоку
* Улыбка
* Глаза
* Тело в полный рост
* Морда кота

К каждому каскаду известен `относительный путь`, цвет, которым отрисовывает файл `run.py`, и флаг `draw`, который позволяет использовать данный каскад файлу `run.py`.

На текущий момент `лица` будут иметь `красные` прямоугольники, все остальные - `зеленые`.

`Улыбка`, `Тело в полный рост` и `Морда кота ` на текущий момент неактивны. Если вам нужны именно эти `каскады` или какой-то один тип среди активных, то вы можете поменять значение `draw` на `True` или `False`.

## Папка haarcascades
Содержит выбранные каскады, а также другие их типы.

## Запуск
Используем команду:
```
python run.py
```
