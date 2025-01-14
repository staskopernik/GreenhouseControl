# Control for GreenHouse on the Arduino
* [Project Description](#chapter-0)
* [Project folders](#chapter-1)
* [Wiring diagrams](#chapter-2)
* [Materials and components](#chapter-3)
* [How to download and flash](#chapter-4)
<a id="chapter-0"></a>
## Project Description
**GreenHouse Control** - universal controller-timer for a greenhouse, incubator, aquarium, apartment, house and other places where automation is needed by a timer or microclimate indicators / other sensors.
   
#### Peculiarities:
- 10 control channels. Of these (in various combinations):
	- 9 каналов с логическим выходом 5V, к которым можно подключать обычное реле, твердотельное реле, силовые ключи (транзисторы, модули на основе транзисторов)
	- 2 канала сервоприводов, подключаются обычные модельные серво больших и маленьких размеров
	- 2 канала ШИМ с высокой частотой (1 кГц) для управления скоростью моторов, яркостью светодиодных лент, мощностью обогревателей
	- 2 канала ШИМ с низкой частотой (1 Гц) для управления мощностью обогревателей
	- 1 канал управления линейным электроприводом с концевиками ограничения движения и работой по тайм-ауту
- Бортовой датчик температуры и влажности воздуха (BME280)
- 4 канала для датчиков, могут работать в разных сочетаниях:
	- 4 аналоговых датчика (влажности почвы или любых других)
	- DHT11/DHT22 – цифровой датчик температуры и влажности
	- Термистор – аналоговый датчик температуры
	- DS18b20 (Dallas) – цифровой датчик температуры. Возможна установка нескольких (с версии 1.6)
	- MH-Z19 – датчик углекислого газа (с версии 1.5)
- Модуль опорного (реального) времени RTC DS3231 с автономным питанием
- Большой LCD дисплей (LCD 2004, 20 столбцов, 4 строки)
- Орган управления - энкодер
- Периодичный полив (реле)
- Схема с индивидуальными помпами/клапанами
- Схема с одной помпой и несколькими клапанами
- Полив на основе показаний датчиков влажности почвы
- Управление освещением (реле) с привязкой ко времени суток
- Проветривание (привод открывает окно/серво открывает заслонку) по датчику температуры или влажности воздуха
- Увлажнение (включение увлажнителя) по датчику влажности воздуха
- Обогрев (включение обогревателя) по датчику температуры
- Выполнение действий сервоприводом (нажатие кнопок на устройствах, поворот рукояток, поворот заслонок, перемещение предметов) по датчику или таймеру
- Режимы:
	- Таймер – простой периодический таймер
	- Таймер RTC – периодический таймер с привязкой к реальному времени
	- Неделька – работа в выбранный промежуток времени в выбранные дни недели
	- Сенсор – релейная работа по выбранному датчику с настройкой периода опроса и гистерезисом
	- ПИД – регулятор для высокоточного поддержания заданного значения с датчика
	- Рассвет – плавное включение и выключение (закат) источника освещения в выбранное время
- Дополнительные фишки:
	- Расписание ПИД регулятора
	- Автотюнер коэффициентов ПИД

<a id="chapter-1"></a>
## Папки
- **libraries** - библиотеки проекта. Заменить имеющиеся версии
- **firmware** - прошивки для Arduino
- **schemes** - схемы подключения компонентов
- **docs** - документация, картинки
- **PCB** - файлы печатной платы

<a id="chapter-2"></a>
## Схемы
![SCHEME](https://github.com/AlexGyver/gyverControl/blob/master/schemes/scheme1.jpg)
![SCHEME](https://github.com/AlexGyver/gyverControl/blob/master/PCB/PCBmap.jpg)
<a id="chapter-4"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**
* Установить библиотеки в  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86)
* **Подключить внешнее питание 5 Вольт**
* Подключить Ардуино к компьютеру
* Запустить файл прошивки (который имеет расширение .ino)
* Настроить IDE (COM порт, модель Arduino, как в статье выше)
* Настроить что нужно по проекту
* Нажать загрузить 

## Settings on the code
    #define ENCODER_TYPE 1      // тип энкодера (0 или 1). Если энкодер работает некорректно (пропуск шагов/2 шага), смените тип
    #define ENC_REVERSE 0       // 1 - инвертировать направление энкодера, 0 - нет
    #define DRIVER_LEVEL 1      // 1 или 0 - уровень сигнала на драйвер/реле для привода
    #define LCD_ADDR 0x3f       // адрес дисплея 0x27 или 0x3f . Смени если не работает!!
<a id="chapter-5"></a>
