# Определение перспективного тарифа для телеком компании

Целью данного исследования является по имеющимся данным определить, какой тариф является для компании наиболее прибыльным.

[Исследование](https://rusmux.github.io/yandex-tariffs/)

[Jupyter-ноутбук](https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb)

<br>

<p align="center"><img src="https://github.com/rusmux/yandex-tariffs/blob/main/cities_clustering.png" height="auto" width=800/></p>
<h6 align="center">Использование PCA/TSNE кластеризации для анализа городов</h6>

<br>


**План:**

<div class="toc">
   <ul class="toc-item">
      <li><span><a href=https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Setup-2">Setup</a></span></li>
      <li><span><a href=https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Вспомогательные-функции-3">Вспомогательные функции</a></span></li>
      <li><span><a href=https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Обработка-данных-4">Обработка данных</a></span></li>
      <li><span><a href="https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Исследовательский-анализ-данных-5">Исследовательский анализ данных</a></span></li>
      <li><span><a href=https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Проверка-гипотез-6">Проверка гипотез</a></span></li>
      <li><span><a href=https://github.com/rusmux/yandex-tariffs/tree/main/Yandex.Tariffs.ipynb data-toc-modified-id="Итог-7">Итог</a></span></li>
   </ul>
</div>
         
<br>

**Итог:**

В результате можно сказать, что средняя прибыль от тарифа ultra выше, чем от тарифа smart, так что компании выгоднее продвигать тариф ultra. Однако, у тарифа ultra, вероятно, чуть больше отток клиентов. Существенной разницы между Москвой и другими городами не обнаружилось, и в принципе между городами не наблюдается сильных различий. 

<br>

**Структура данных:**

Информация о тарифах хранится в файле `tariffs.csv`:


* `tariff_name` — название тарифа


* `messages_included` — количество сообщений в месяц, включённых в абоненскую плату


* `mb_per_month_included` — количество мегабайт интернета в месяц, включённых в абоненскую плату


* `minutes_included` — количество минут разговора в месяц, включённых в абоненскую плату


* `rub_monthly_fee` — ежемесячная абоненская плата в рублях


* `rub_per_gb` — стоимость одного дополнительного гигабайта интернета сверх тарифного плана


* `rub_per_message` — стоимость отправки одного дополнительного сообщения сверх тарифного плана


* `rub_per_minute` — стоимость одной дополнительной минуты разговора сверх тарифного плана


Данные о звонках клиентов находятся в файле `calls.csv`:


* `id` — уникальный идентификатор звонка


* `call_date` — дата звонка


* `duration` — длительность звонка в минутах


* `user_id` — идентификатор клиента


Информация об интернет-сессиях сохранена в файле `internet.csv`:


* `id` — уникальный идентификатор сессии


* `mb_used` — количество мегабайт, использованных за сессию


* `session_date` — дата сессии


* `user_id` — идентификатор клиента


Данные об отправленных сообщениях находятся в файле `messages.csv`:


* `id` — уникальный идентификатор сообщения


* `message_date` — дата отправления сообщения


* `user_id` — идентификатор пользователя


Информация о клиентах телеком-компании хранится в файле `users.csv`:


* `user_id` — уникальный идентификатор пользователя


* `age` — возраст пользователя в годах


* `churn_date` — дата прекращения пользования тарифом (если значение пропущено, то тариф еще действовал на момент выгрузки данных)


* `city` — город проживания пользователя


* `first_name` — имя пользователя


* `last_name` — фамилия пользователя


* `reg_date` — дата подключения тарифа


* `tariff` — название тарифного плана	
