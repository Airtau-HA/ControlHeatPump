# ControlHeatPump
Контроллер теплового насоса

Открытый проект "Народный контроллер" для тепловых насосов.<br>
Данное програмноое обеспечение предназначено для управления<br>
различными типами тепловых насосов для отопления и ГВС.<br>
<br>
Подробное обсуждение проекта на форуме: <br>
https://www.forumhouse.ru/threads/352693/ <br>
https://www.forumhouse.ru/threads/437182/

Изменения по версиям: <br>
Версия 0.966
1. Обновление текстовых файлов
2. Добавлено описание ТН, исправлены ошибки для компиляции 1 конфига
3. Работа над статистикой с записью ее на SD карту
4. Фикс бага инициализации nextion если он находится в спящем режиме
5. Мелкие уточнения в веб морде
6. Обновление 2 конфига и уточнение типа ошибки при пуске компрессора
7. Добавлен еще один алгоритм разморозки без датчика разморозки по температурам. Автор Pskovsat

Версия 0.965
1. Реализована возможность загрузки и работы с веб мордой на чипе spi flash.В опциях есть флаг загрузки из него
2. Оптимизация работы АЦП

Версия 0.964
1. Исправления ошибок в алгоритме работы ТН
2. Оптимизация работы АЦП
3. Оптимизация функции прерывания АЦП

Версия 0.963
1. Добавление spi диска
2. Частично сделана загрузка файлов через веб в spi диск (еще нужно причесать код и контроль ошибок)
3. Опция переключения места хранилища для веб-сервера
4. Доделка загрузки веб морды через веб в spi диск Есть проблемы при загрузке множества файлов (потеря пакетов)
5. Обновление дисплея Nextion, включая его прошивку
6. bugsfixs, добавлен редактор Nextion
7. Оптимизация длин неоторых запросов
8. Оптимизация стека RTOS

Версия 0.962
1. Изменены: структура сохранения, библиотека RTC, нумерация профилей в вебе, и др.
2. Nextion code changed
3. Nextion class rework
4. Исправлена ошибка с выводом сообщений при ошибках в классе HeatPump
5. Расписание теперь всегда компилится
6. Начало работы над загрузкой веб морды в spi Сделано декодирование имени и размера загружаемого файла
7. Сделан для post запросов разбор заголовка определение имени и длины файла и определение размеров первого (принятого) куска файла
8. Nextion update

Версия 0.961
1. Перенос SPI_RATE -> config.h
2. Замена библиотеки SdFat, функция тестирование скорости SD карты (/TEST_SPEED:<имя файла>)
3. Оптимизации библиотеки SdFat
4. Установка скорости SD в МГц - #define SD_CLOCK 24

Версия 0.960
1. Поддержка ИБП на контроллер
2. На страницу "Файлы" добавлены элементы для выбора файлов для копирования в spi eeprom
3. Исправлена ошибка с upload files
4. Имена аналоговых датчиков перенесены в config
5. Исправление ошибки вывода на график частотных датчиков
6. Добавлена опция - СК регенерирует ГК в простое ТН
7. Оптимизация закладки тест
8. Оптимизация СК, конфиг vad7, дефайн DEBUG_MODWORK
9. Настройки СК

Версия 0.959
1. Оптимизация web, выложена схема платы Добрыни
2. Замена в SDK DUE - добавлен класс UART
3. Исправлена ошибка с RPUMPBH
4. Исправлена ошибка с radio_sensor
5. Добавлена схема K-Line адаптера, небольшие фиксы
6. Исправлена ошибка с edit strings

Версия 0.958
1. Солнечный коллектор на плане (картинка)
2. Обновление первого конфига до текущей версии (cтарт-стоп компрессор с ТРВ переливная схема)
3. Включенное реле вручную на странице тестирование можно выключить только на ней, в не зависимости от текущей или будующей работы ТН.
4. Настройка через Config.h какие датчики температуры выводить на страницу "Схема", в const uint8_t SENSORTEMP[TNUMBER]={...} нужно поставить 2, у нужного датчика.
5. Изменение целевых температур бойлера и отопления на дельту по часам, для эффективного использования ночного тарифа
6. Условие расчета КОП (работа компрессора) определяется #define COP_ALL_CALC
7. На github выложена информация по дисплею Nextion
8. На github выложена информация по WiFi устройству (датчик температуры)
9. Проверка состояния частотника только перед его непосредственным стартом.
10. Добавлена опция "Однократный поиск "0" ЭРВ" Настройки ЭРВ из "Опций" перенесены в "Настройки ЭРВ"
11. Оптимизация парсера для вывода графика
12. "Причесывание" надписей на веб морде
13. Фикс бага для датчиков Wifi (откат формата uptime к виду 00d 00h 00m) Обновление морды удаленного датчика wifi
14. Оптимизация веб (датчики), температура
15. Поддержка радиодатчиков ZONT МЛ‑703


Версия 0.957
1. Опция "теплый пол" в профилях - управляет насосом RPUMPFL
2. Опция - расписание ГВС только для ТЭНа бойлера
3. Изменение режима турбо ГВС. Теперь при включении турбо+догрев ГВС греетеся ТН+ТЭН до температуры догрева далее только ТЭН
4. Фикс работы насосов (в схеме без трехходового) для режима пауза
5. Чтение настроек из файла (в новом формате)
6. Фикс алгоритма Сальмоннеллы
7. Фикс блокировки семафорора для 485 порта (уменьшена загрузка CPU при работе ТН)
8. Фикс сброса сетевой карты
9. Добавлена возможность работы с солнечным/воздушным коллектором (#define USE_SUN_COLLECTOR)

Версия 0.956
1. Оптимизирована запись в журнал, радиодатчики - начало.
2. max/min sensorADC
3. Включение RPUMPO при переключение с бойлера на отопление
4. Фикс ошибки при выходе из нагрева ГВС при срабатывании защиты
5. Cохранение в файл в новом формате
6. Опция логировать работу частотника
7. Фикс при переходе нагрева бойлера на тэн
8. Опциональное вычисление для TIN среднего и/или минимального значения среди других датчиков
9. Фикс расчета перегрева при охлаждении, фикс работы бойлера (переключение на дом)

Версия 0.955
1. Оптимизация работы oneWire
2. Ускоренный поиск датчиков температуры
3. Неограниченное кол-во DS18x20, исправление ошибки в DUE UART

Версия 0.954
1. Оптимизация графиков
2. Ethernet lib fix (зацикливание при передаче MQTT)
3. Расчет графиков powerCO powerGEO на лету, фикс вывода графиков в файл
4. Синхронизация времени по HTTP GET с esp8266 веб-сервера (отдельное устройство vad711),
5. Изменен блок статусов, опция не проверять CRC у DS18B20, изменены единицы работы насосов в паузе на сек, изменены настройки датчиков протока, багфиксы.
6. Индикация тэна и насоса бойлера на странице схема, багфиксы
7. Возможность использовать 4 шины датчиков температуры, 3 из них могут быть двухпроводные.
8. В файл настроек в текстовом виде, добавлен вывод новых (пропущеных) параметров
9. Доработка по шинам температуры на DS2482, добавлен режим чтения аналоговых датчиков через модбас
10. Фикс разморозки воздушника + описание в части датчиков температуры
11. Сохранение без потери настроек при изменении структуры
12. Поддержка датчиков ds18s20

Версия 0.953
1. Веб морда добаление дополнительных параметров на схему ТН
2. Возможность скрытия логирования ошибок чтения счетчика SDM120
3. Оптимизация библиотеки Модбас в части работы с портом
4. Дополнительные флаги для датчиков температуры (логирование и игнорирование ошибок)
5. Оптимизация чтения датчиков и modbus, вывод частоты сети 220 в веб.
6. Вывод мощности CO, доработка Vacon
7. Доработка корректировки перегрева, исправление ошибок  модбас, ваком
8. Оптимизация парсера - удаление из парсеров параметров которые только на чтение
9. Фикс восстановления настроек инвертора Омрон (флаги)
10. Небольшие переделки страницы ЭРВ
11. Добавлен график 20, 30 сек, небольшая оптимизация парсера
12. Фикс для охлаждения датчик TCONOUT и фикс расчета мощностей и СОРов для охлаждения
13. Доработка корректировки перегрева
14. Оптимизации работы с ftoa itoa, удаление функции int2str
15. В config настройка задержки после переключения насосов
16. Оптимизация чтения счетчика SDM
17. Оптимизация функций DecodeTimeDate и StatDate, фикс ошибок парсера реле
18. Фикс ошибки старта насоса при догреве(только)
19. Расчет мощностей и СОР всегда (раньше было только при работе)
20. Vacon расчет номинальной мощности
21. Доработка страницы ЭРВ, фикс ПИД эрв
22. фикс передачи на MQTT сервер
23. Мощность частотника в Вт
24. Vacon - авто-очистка сбоя, очередь из 1 команды, оптимизация, раздельный останов насосов по дефайну и др.
25. Возможность выключить ТН из отложенного запуска/рестарт по ошибке
26. Для Омрона отдельная страница настроек (гц) - надо копировать
27. Перенос флага включения ТН в счетчики, теперь профиль реже пишутся
28. Дельта коррекции перегрева считается от стартового перегрева

Версия 0.952
1. Добавлено в управление ЭРВ возможность корректировки перегерва в зависмости от разницы температур испарителя и конденсатора
2. Оптимизация сохранения ЭРВ
3. Фикс: DHСP, датчики температуры. Оптимизация веба.
4. Опция - один датчик на 2-ой шине 1-Wire, для уменьшения влияния помех (измененен формат сохранения: 123)
5. DNS по TCP (выбор автоматически), доработка сетевой либы, оптимизация журнала и др.
6. Начало переделки парсера запросов с целью его оптимизации и увеличения скорости.
7. В класс ЭРВ добавлы настройки (из дефайнов) и оптимизировано сохранение (единая структура настроек)
8. В класс FC добавлы настройки (из дефайнов) и оптимизировано сохранение (единая структура настроек) (измененен формат сохранения: 125)
9. В опции ТН добавлены настройки времен, парсер опций переделан

Версия 0.951
1. Доработка веб, перенос настроек в config, исправление багов
2. Доработка страницы тестирования
3. Добавлен расчет переохлаждение на схеме ТН

Версия 0.950
1. Доработка 1-Wire, багфиксы, новая ошибка ERR_ONEWIRE_RW - ошибка во время чтения/записи OneWire
2. Фикс библиотеки DUE для доступности портов D53,D69
3. Доработка I2C init
4. Оптимизация Web-modbus

Версия 0.949
1. Оптимизация использования стека в itoa, vsnprintf, ftoa cj,собсвенная функция printf
2. Patch Arduino board SAM library for optimized itoa() function
3. Добавлен насос нагрева ГВС RPUMPBH (не циркуляции ГВС)
4. Фикс отображения включения ТН во время паузы
5. Добавлена кнопка сброса статистики задач free RTOS
6. Исправлена ошибка перехода в режим Ожидания по расписанию
7. Для экономии памяти теперь графики расчета разности температур ПТО рассчитываются в момент запроса
8. Добавлен насос теплых полов RPUMPFL (в режиме охлаждения не включается)
9. Перевод FLOWPCON в не обязательный параметр
10. Автоскрытие аналогового управления инвертером, насоса ТП
11. Доработка по инвертору Vacon (режим тест)

Версия 0.948
1. Уменьшение потребление стека RTOS
2. Фикс ожидания DHCP, оптимизация сетевой либы

Версия 0.947
1. При инициализации сетевого чипа добавлена проверка на соединение сетевым кабелем (link)
2. Переделан код обслуживания ТЭНа бойлера, теперь он сосредоточен в одном месте
3. Оптимизация и переименование кода для переключения между ГВС и отоплением/охлаждением (поддержка управления насосами для переключения)
4. Исправлена ошибка с сохранением/восстановлением настроек в бинарный файл
5. Доделана и протестирована страница Modbus (можно читать/сохранять регистры)
6. Сделан алгоритм обеззараживания (сальмонелла) для ГВС
7. Исправлена ошибка в расписании ГВС

Версия 0.946
1. Исправлена ошибка отображения графика потока конденсатора
2. Исправлена ошибка вывода в текстовый файл настроек (коэффициент для аналогового датчика)
3. Исправлена ошибка управленем догревом бойлера - алгоритм перенесен в другое место
4. Исправлена ошибка в режиме тест для датчиков потока
5. Настройки догрева бойлера перенесены в раздел ГВС из опций (откорректированы имена параметров запросов)
6. Сделан вывод специфических ошибок для Vacon 10 и пофиксены некоторые ошибки
7. Добавлена возможность проверки потоков на минимальные значения перед включением компрессора (#define FLOW_CONTROL)
8. Доработана морда для сканирования после изменения работы шины OneWire, в новой версии увеличилось время сканирования.
9. Дмитрий обновил мобильную морду
10. Добавлен функционал модификации имен запрашиваемых файлов, теперь в зависимости от конфига показываются на морде разные схемы.
11. В работу ТН добавлены внутренние команды WAIT и RESUME для обеспечения функционала расписания, теперь если в расписании дырка (нет профайла) то ТН будет находится в сосоянии "Ожидание"
12. ТЕСТ страничка с чтением/записью произвольных ячеек Modbus RTU

Версия 0.945
1. R3WAY переведен в необязательный, теперь можно компилировать без него
2. При переключениеи с ГВС сделано временное отключение (#define DELAY_BOILER_OFF) части защит, на время остывания ТН.
3. Немного переделана функция вывода ошибок, теперь где актуально выводится имя функции в которой произошла ошибка
4. В уведомлениях почты убран вывод устройство которых нет в текущей конфигурации (если стоит флаг выводить подробности)
5. Исправлен и добавлен вывод настроек ТН в текстовом виде (дабавлены настроки тарифов)
6. Проведено переименование констант, переменных и функция инвертора  в нейтральные (без упоменния ОМРОН и МХ2)
7. Добавлена поддержка трехфазного счетчика SDM630 (vad711) (определить #define USE_SDM630)
8. Класс частотный преобразователь был стандартизован (все аппартано зависимые функции спрятаны внутрь класса) для возможности подключения других инверторв короме Omrona
9. vad711 добавил поддержку инвертора Vacon 10 по модбасу.
10. Исправлена ошибка подсчета общего числа ошибок чтения датчиков температуры
11. Переделана блокировка задачи циркуляционного насоса отопления в паузах
12. Исправлена ошибка вывода информации при старте ТН
13. Переделан механизм работы с датчиками температуры. Теперь разрешено три вида шин OneWire и одновременно может присутвовать три вида шин в контроллере.
14. Добавлено расписание работы (пока не до конца)
15. Переделан вид расписания бойлера на веб морде
16. Добавлена страница на вебморду для вывода информации по задачам операционной системы (главное - минимальный размер стека)
17. Часть нагрузки из задачи "бездействия" перенесено в задачу чтения датчиков
18. На морде в профилях сделано обновление данных при изменении параметров профиля
19. В связи с работой над расписаниями, удален функционал тарифов день/ночь
20. Исправена ошибка вывода числа ошибок чтения температурных датчиков.
21. Добавлен ввод теплоемкости теплоносителя в контурах где стоят расходомеры (изменилась версия сохранения)
22. Переделана размерность коэффициентов пересчета расходомеров, теперь она в имп/литр
