# Исследование рынка общественного питания Москвы

Данное исследование ставит перед собой цель по открытым данным проанализировать рынок заведений общественного питания Москвы.

<a href="https://rusmux.ml/yandex-projects/7-restaurants.html" target="_blank">Исследование</a>

<a href="Yandex.Restaurants.pdf" target="_blank">Презентация по исследованию</a>

В исследовании используются внешние данные, получение которых может суммарно занять до 60 минут. Для удобства эти данные были сохранены в файлах `google_data.csv` и `mapbox_data.csv`. Код для получения этих данных был закомментирован, для самостоятельного получения данных раскомментируйте его.


<p align="center"><img src="images/1.png"></p>
<h6 align="center">Распределение типов для сетевых и одиночных заведений</h6>

<p align="center"><img src="images/2.png"></p>
<h6 align="center">Топ-10 сетей по количеству заведений</h6>

<br>

<p align="center"><img src="images/4.png"></p>
<h6 align="center">Топ-10 самых популярных улиц по количеству заведений</h6>

**План:**

<div class="toc">
   <ul class="toc-item">
      <li><span><a href="#Setup" data-toc-modified-id="Setup-2">Setup</a></span></li>
      <li>
         <span><a href="#Предобработка-данных" data-toc-modified-id="Предобработка-данных-3">Предобработка данных</a></span>
         <ul class="toc-item">
            <li>
               <span><a href="#Обработка-адресов" data-toc-modified-id="Обработка-адресов-3.1">Обработка адресов</a></span>
               <ul class="toc-item">
                  <li><span><a href="#Google-geocoding" data-toc-modified-id="Google-geocoding-3.1.1">Google geocoding</a></span></li>
                  <li><span><a href="#Mapbox-reverse-geocoding" data-toc-modified-id="Mapbox-reverse-geocoding-3.1.2">Mapbox reverse geocoding</a></span></li>
               </ul>
            </li>
            <li><span><a href="#Обработка-названий-заведений" data-toc-modified-id="Обработка-названий-заведений-3.2">Обработка названий заведений</a></span></li>
            <li><span><a href="#Обработка-дубликатов" data-toc-modified-id="Обработка-дубликатов-3.3">Обработка дубликатов</a></span></li>
            <li>
               <span><a href="#Обработка-аномалий" data-toc-modified-id="Обработка-аномалий-3.4">Обработка аномалий</a></span>
               <ul class="toc-item">
                  <li><span><a href="#Сетевые-заведения" data-toc-modified-id="Сетевые-заведения-3.4.1">Сетевые заведения</a></span></li>
                  <li><span><a href="#Тип-заведения" data-toc-modified-id="Тип-заведения-3.4.2">Тип заведения</a></span></li>
                  <li><span><a href="#Количество-посадочных-мест" data-toc-modified-id="Количество-посадочных-мест-3.4.3">Количество посадочных мест</a></span></li>
               </ul>
            </li>
         </ul>
      </li>
      <li>
         <span><a href="#Исследовательский-анализ-данных" data-toc-modified-id="Исследовательский-анализ-данных-4">Исследовательский анализ данных</a></span>
         <ul class="toc-item">
            <li><span><a href="#Доля-сетей-на-рынке" data-toc-modified-id="Доля-сетей-на-рынке-4.1">Доля сетей на рынке</a></span></li>
            <li><span><a href="#Типы-заведений" data-toc-modified-id="Типы-заведений-4.2">Типы заведений</a></span></li>
            <li><span><a href="#Доля-сетей-по-типу-заведения" data-toc-modified-id="Доля-сетей-по-типу-заведения-4.3">Доля сетей по типу заведения</a></span></li>
            <li><span><a href="#Топ-сети" data-toc-modified-id="Топ-сети-4.4">Топ-сети</a></span></li>
            <li><span><a href="#Распределение-мест" data-toc-modified-id="Распределение-мест-4.5">Распределение мест</a></span></li>
            <li><span><a href="#Распределение-по-округам" data-toc-modified-id="Распределение-по-округам-4.6">Распределение по округам</a></span></li>
            <li><span><a href="#Распределение-по-улицам" data-toc-modified-id="Распределение-по-улицам-4.7">Распределение по улицам</a></span></li>
            <li><span><a href="#Местоположение-топ-сетей" data-toc-modified-id="Местоположение-топ-сетей-4.8">Местоположение топ-сетей</a></span></li>
         </ul>
      </li>
      <li><span><a href="#Итог" data-toc-modified-id="Итог-5">Итог</a></span></li>
   </ul>
</div>

<br>

**Выводы:**

Были даны открытые данные о заведениях общественного питания Москвы. Данные содержали множественные неточности и дубликаты, так что была проведена предобработка, которая включала в себя обработку названий заведений, типов объектов и адресов. Для получения точных адресов и координат объектов использовались сервисы Google Maps и Mapbox. 

&emsp; *Типы заведений*

* Кафе занимают ~40% рынка. Потом идут столовые (17%), рестораны (14%) и предприятия быстрого обслуживания (14%). <br> Остальные типы заведений составляют меньше 15% рынка.

&emsp; *Сети*


* Сетевые заведения составляют ~20% всех заведений. Практически 80% всего рынка занимают одиночные заведения.<br> Половина предприятий быстрого обслуживания являются сетями. Примерно четверть кафе и ресторанов - сети. Среди остальных типов заведений доля сетей незначительна.


* 52% всех сетей являются кафе;<br>
  32% являются ПБО;<br>
  14% являются ресторанами.
  
&emsp; *Топ-сети*

* Топ-сети обладают от 10 до 180 заведениями. Больше всего в среднем заведений у сетей предприятий быстрого обслуживания — от 60 до 170. У кафе немного меньше — от 40 до 100. Ресторанов обычно от 10 до 50.

&emsp; *Количество мест*

* В столовых и ресторанах порядка 80-100 сидячих мест;<br>
  В барах, буфетах и кафе – 30;<br>
  В ПБО относительно немного мест – меньше 10.<br>
  У самых популярных сетей в среднем по 15-50 мест. Но есть заведения и с малым количеством мест, а также заведения навынос.

&emsp; *Округа*

* По количеству заведений лидируют центральные округа Москвы. Особенно много заведений в Тверском и Пресненском округах.<br> Топ-10 округов занимают ~30% всего рынка.<br>

  Топ-7 округов:

&emsp;&emsp;&emsp; 1) Тверской<br>
&emsp;&emsp;&emsp; 2) Пресненский<br>
&emsp;&emsp;&emsp; 3) Басманный<br>
&emsp;&emsp;&emsp; 4) Даниловский<br>
&emsp;&emsp;&emsp; 5) Хамовники<br>
&emsp;&emsp;&emsp; 6) Таганский<br>
&emsp;&emsp;&emsp; 7) Мещанский<br>


* Самая низкая плотность заведений в подмосковных округах.

&emsp; *Улицы*

* На самых популярных улицах расположено от 80 до 170 заведений.<br>
  
  Топ-7 улиц (больше 100 объектов):
  
&emsp;&emsp;&emsp; 1) Профсоюзная улица<br>
&emsp;&emsp;&emsp; 2) Проспект Мира<br>
&emsp;&emsp;&emsp; 3) Варшавское шоссе<br>
&emsp;&emsp;&emsp; 4) Пресненская набережная<br>
&emsp;&emsp;&emsp; 5) Ленинградский проспект<br>
&emsp;&emsp;&emsp; 6) Проспект Вернадского<br>
&emsp;&emsp;&emsp; 7) Кировоградская улица<br>

**Рекомендации:**

<ins>Тип заведения:</ins> &ensp;**кафе** или **предприятие быстрого обслуживания**. 

В рестораны ходят уже взрослые, мало впечатлительные люди, которые новизне предпочитают скорость и качество. После того как угаснет ажиотаж вокруг новой технологии людям быстро докучит несговорчивый и мало эмоциональный "официант". Как правило, официант может с улыбкой рассказать про блюда, вина, ответить на вопросы и запомнить специфичные детали заказа. 

Железный официант мало впишется в бар по аналогичным причинам, а кафетерии и магазины мы не рассматриваем — это слишком редкий тип заведения. Столовые не являются сетевыми.

В кафе или предприятии быстрого обслуживания официант играет не такую существенную роль, как в ресторане. Если сделать роботов дружелюбными, то они вполне могут прийтись по душе детям в кафе, а в предприятии быстрого обслуживания они могут стать быстрыми и неназойливыми. Кроме того, кафе и ПБО — одни из самых частых типов заведений.

<ins>Количество мест:</ins> &ensp;**30-50**. В данном вопросе лучше довериться опыту. В среднем у топ-сетей кафе и ПБО от 30 до 60 сидячих мест. Можно начать с золотой середины — 40 мест, чтобы не создавать очень большую нагрузку в самом начале, но и не сокращать сильно места. Лучше сначала опробовать свои силы, а потом уже расширяться.

<ins>Округ:</ins> &ensp;любой **центральный округ**. Чтобы набрать популярность в первые месяцы, необходимо быть у людей на виду. Вряд ли сеть раскрутится в Одинцово. Дальше можно продолжить распространение равномерно по всей Москве, как у топ-сетей.

В моем представлении, это что-то похожее на Макдоналдс или Шоколадницу.

<img src="images/3.png">

<br>

**Структура данных:**

Информация о заведениях общественного питания находится в файле `rest_data.csv`:

* `id` — уникальный идентификатор объекта;

* `object_name` — название заведения;

* `chain` — является ли заведение сетью;

* `object_type` — тип объекта;

* `address` — адрес заведения;

* `number` — количество посадочных мест.

Данные, полученные с помощью API Google Cloud Platform, сохранены в файле `google_data.csv`:

* `id` — уникальный идентификатор объекта;

* `google_address` — адрес заведения, полученный с помощью API Google Cloud Platform;

* `google_address_translated` — google-адрес, переведенный на русский через Google Переводчик;

* `latitude` — географическая ширина, полученная с помощью API Google Cloud Platform;

* `longitude` — географическая долгота, полученная с помощью API Google Cloud Platform.

Данные, полученные с помощью API Mapbox, сохранены в файле `mapbox_data.csv`:

* `id` — уникальный идентификатор объекта;

* `place` — регион/город заведения, полученный с помощью API Mapbox;

* `locality` — район, полученный с помощью API Mapbox;

* `street` — название улицы, полученное с помощью API Mapbox.

Названия заведений, переведенные на русский с помощью Google Переводчика, находятся в файле `object_names_translated.csv`:

* `id` — уникальный идентификатор объекта;

* `object_name` — название заведения, переведенное на русский с помощью Google Переводчика.
