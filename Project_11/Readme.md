# Определение успешности стартапа.

## Введение.

По данным собранным о стартапах с 1970 года необходимо предсказать жизнеспособность стартапа. Предоставленны данные о географическом положении стартапа, о его области разработки, о раундах финансирования и о суммме финансирования. Данные предоставлены реальные с примесью синтетических данных неизвестного происхождения. 

## Оснонвная работа.

Вся работа была проведена в jupyter notebook на языке программирования python с использованием популярных бибилиотек для data science. Данные предоставленны онлайн сервисом Kaggle. 

### Загрузка и ознакомление с данными.

После скачивания данных они были загружены в ноутбук в виде датасетов. Сырые даные имели тем не менее нормальное название столбцов. Базовая информация показала присутствие значительного количества пропусков в нектороых столбцах. Общий объём данных превышал 52 тысячи записей  и имел 13 полей.

### Предварительная предобработка данных.

В датасете, кроме обычных данных, были и очевидные утечки. Одно из полей содержало информацию о дате закрытия стартапа - таких данных не должно быть в обучающей выборке. Нам известен момент выгрузки датасета - 2018 год. Поэтому сразу создадим столбец о времени жизни стартапа на момент выгрузки данных в днях. 

Полных дубликатов в даных обнаружено не было. Достойный результат, учитывая объём данных. А вот пропусков достаточно много, их придётся заполнить различными способами. 

### Поцноценный разведочный анализ.

Первая общая информация о данных показала слишком много уникальных значений в некоторых категориальных столбцах. Чтобы оценить значимость самых популярных категорий, посмотрим распределение значений целевого признака в разрезе этих категорий. Результат показал, что область развития стартапа не является значимой для целевого признака. Геоданне тоже имеют много уникальных значений. Политика и традици в отношении стартапа больше исходят из страны, поэтому в планах оставить только данные о стране. Это мы ещё узнаем их корреляционнного анализа.

Числовые данные и данные формата даты не показали ничего необычного, кроме достаточно сильного разброса и аномальных значений. С полями даты лучше не работать модели, мы из них изготовим новые поля.

### Новые поля.

Создадим новые поля. Среди них будут средняя сумма финансирования за один раунд, время активного финансирования в днях, год начала финансирования, год последнего рануда финансирования, категоризация количства раундов финансирования, категоризация времени жизни стартапа.

### Проведение корреляционного анализа.

Проведение корреляционного анализа затрудняется большим количеством данных. Поэтому на этом этапе мы вопспользуемся техникой bootstrap. Из нашей выборки возьмём подвыборки и посчитаем на них корреляционную матрицу. После этого подсчитаем средние значения в матрице. 

Результат показал мультиколлинеарность полей геоданных. Откажемся от лишних столбцов и оставим только код страны.

### Обучение.

Финальная подготовка данных и обучение различных моделей будет происходить в пайплайне, который мы подготовили. В пайплайне использованы различные модели классификации. Лучшей моделью оказалась модель дерева решений. Целевая метрика f1 имеет значение свыше 0.95, что означает хороший результат.

### Анализ важности признаков.

Анализ важности признаков показывает, какие поля были для модели важны при классификации. Оценка важности признаков для модели показала, что ключевую роль играет время жизни стартапа в днях и год последнего раунда финансирования. На втором плане стоит год первого раунда финансирования, время активного финансирования и код страны.

## Заключение.

В ходе выполнения данного data science исследования были проведены анализ данных, построены модели и получены результаты, которые позволили выявить закономерности и тенденции по изучаемой теме. Полученные результаты представляют ценную информацию для принятия решений и разработки стратегий в соответствующей области. В целом, исследование позволило получить полезные знания и видение текущей ситуации, что является важным шагом на пути к осуществлению поставленных целей.