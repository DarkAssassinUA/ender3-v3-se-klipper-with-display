# Ender 3 V3 SE Klipper with Display (Merged Repository)

> **ВНИМАНИЕ:** Это объединенный репозиторий, созданный специально для работы оригинального дисплея Ender 3 V3 SE с самой свежей версией Klipper (от 0xD34D).
> 
> * **Основа (Klipper):** Форк [0xD34D/klipper_ender3_v3_se](https://github.com/0xD34D/klipper_ender3_v3_se) с обновлениями из оригинального [Klipper3d/klipper](https://github.com/Klipper3d/klipper) (Последний коммит: `b7c0329f1`, Май 2026)
> * **Мод дисплея:** Портировано из [jpcurti/ender3-v3-se-klipper-with-display](https://github.com/jpcurti/ender3-v3-se-klipper-with-display) (Последний коммит: `72e925e55`, Январь 2026)

---

## Настройка (Configuration)

Чтобы включить поддержку дисплея, в ваш файл `printer.cfg` необходимо добавить секцию `[e3v3se_display]`. Кроме того, вы можете установить пользовательский язык и включить логирование (по умолчанию используются английский язык и logging: False), например:

```yaml
[e3v3se_display]
language: english # Проверен английский и русский, остальные языки не проверялись.
logging: False
```

### Пользовательские макросы (Custom macros)

Новое меню 'Misc' содержит список пользовательских макросов, которые можно задать в вашем `printer.cfg`.
Вы можете использовать это для запуска макросов Klipper прямо с экрана принтера, например: загрузка/выгрузка филамента, калибровка Z-смещения, калибровка уровня стола, очистка сопла и т.д.

В файле `printer.cfg` макросы можно задать с помощью новой секции `[e3v3se_display MACRO%I]`, где `%i` — это порядковый номер макроса (должен быть уникальным для каждого макроса). Доступны следующие свойства:

| Свойство | Тип данных | Обязательно | Описание                                                       |
|----------|------------|-------------|----------------------------------------------------------------|
| label    | Текст      | Да          | Текст, который будет отображаться на экране                    |
| icon     | Целое число| Нет         | Внутренняя иконка прошивки. По умолчанию 14 (иконка файла)     |
| gcode    | Текст      | Да          | G-код, выполняемый при выборе пункта. Например, `G28` для Home |

Несколько примеров для вдохновения:

```yaml
[e3v3se_display MACRO1]
gcode: LOAD_FILAMENT
label: Загрузить филамент
icon: 14

[e3v3se_display MACRO2]
gcode: UNLOAD_FILAMENT
label: Выгрузить филамент
icon: 14

[e3v3se_display MACRO3]
gcode: CALIBRATE_Z_OFFSET
label: Калибровка Z-смещения
icon: 12
```

Чтобы посмотреть библиотеку доступных иконок, вызовите макрос `ENDER_SE_DISPLAY_ICON_FINDER` в консоли Klipper и с помощью экрана пролистайте все иконки.

## Поддерживаемые функции

На данный момент поддерживаются следующие функции:

| Функция (Feature)         | Статус  |
| ------------------------- | ------- |
| Печать файла              | &check; |
| Настройка во время печати | &check; |
| Пауза / Возобновление     | &check; |
| Остановка печати          | &check; |
| Движение осей             | &check; |
| Парковка осей (Home)      | &check; |
| Установка Z-смещения      | &check; |
| Отключение моторов        | &check; |
| Преднагрев стола          | &check; |
| Охлаждение                | &check; |
| Установка температуры сопла| &check; |
| Установка температуры стола| &check; |
| Изменение макс. скорости  | &cross; |
| Изменение макс. ускорений | &cross; |
| Изменение шагов на мм     | &cross; |
| Ручное меню Z-offset      | &check; |
| Меню кастомных макросов   | &check; |

## Важное замечание

- Этот проект основан на **прошивке дисплея E3V3SE версии 1.0.6**. Любые изменения в версии прошивки дисплея (например, выход новой версии от Creality) могут изменить адреса изображений в памяти дисплея, и потребуется новая настройка маппинга. Список доступных прошивок можно найти на [сайте Creality](https://www.creality.com/pages/download-ender-3-v3-se), а подробная инструкция по обновлению дисплея доступна на [YouTube](https://www.youtube.com/watch?v=8oRuCusCyUM&ab_channel=CrealityAfter-sale).

---

Welcome to the Klipper project!
[![Klipper](docs/img/klipper-logo-small.png)](https://www.klipper3d.org/)

https://www.klipper3d.org/

The Klipper firmware controls 3d-Printers. It combines the power of a
general purpose computer with one or more micro-controllers. See the
[features document](https://www.klipper3d.org/Features.html) for more
information on why you should use the Klipper software.

Start by [installing Klipper software](https://www.klipper3d.org/Installation.html).

Klipper software is Free Software. See the [license](COPYING) or read
the [documentation](https://www.klipper3d.org/Overview.html). We
depend on the generous support from our
[sponsors](https://www.klipper3d.org/Sponsors.html).
