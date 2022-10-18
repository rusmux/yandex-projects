# Исследование надежности заемщиков

Данное исследование ставит перед собой цель проверить:

&emsp; 1. Как количество детей влияет на возврат кредита в срок


&emsp; 2. Есть ли зависимость между семейным положением и возвратом кредита в срок


&emsp; 3. Есть ли зависимость между уровнем дохода и возвратом кредита в срок


&emsp; 4. Как разные цели кредита влияют на его возврат в срок

Результаты исследования будут учтены при построении модели кредитного скоринга — специальной системы, которая оценивает способность потенциального заёмщика вернуть кредит банку.

[Исследование](https://rusmux.github.io/yandex-projects/1-banking.html)

[Jupyter-ноутбук](Yandex.Banking.ipynb)

<br>

<p aling="center"><img src="debt_by_purpose.png"/></p>
<h6 align="center">Вероятность возникновения задолженности в зависимости от цели кредита</h6>

<br>


**План:**

<div class="toc">
   <ul class="toc-item">
      <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Setup-2">Setup</a></span></li>
      <li>
         <span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Предобработка-данных-3">Предобработка данных</a></span>
         <ul class="toc-item">
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Обработка-аномалий-3.1">Обработка аномалий</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Удаление-дубликатов-3.2">Удаление дубликатов</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Декомпозиция-данных-3.3">Декомпозиция данных</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Заполнение-пропусков-3.4">Заполнение пропусков</a></span></li>
         </ul>
      </li>
      <li>
         <span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Исследовательский-анализ-данных-4">Исследовательский анализ данных</a></span>
         <ul class="toc-item">
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Количество-детей-4.1">Количество детей</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Семейное-положение-4.2">Семейное положение</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Уровень-дохода-4.3">Уровень дохода</a></span></li>
            <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Цели-кредита-4.4">Цели кредита</a></span></li>
         </ul>
      </li>
      <li><span><a href=https://github.com/rusmux/yandex-banking/blob/main/Yandex.Banking.ipynb data-toc-modified-id="Итог-5">Итог</a></span></li>
   </ul>
</div>

<br>

**Итог:**

Данные о заемщиках содержали множественные неточности и ошибки. Была проведена обработка аномалий, удаление дубликатов и заполнение пропусков, используя методы машинного обучения.

По итогам исследования можно сделать выводы, что:

1. Люди с большим числом детей (от 4) чаще других не возвращают кредит вовремя


2. Люди, которые когда-либо состояли в браке, реже становятся должниками


3. Возвращение кредита в срок мало зависит от дохода клиента


4. Операции с недвижимостью наиболее безопасный тип кредита для банка. Потом идут проведение свадьбы и получение образования. Самый небезопасный кредит - на приобретение автомобиля

<br>

**Структура данных:**

Данные о заемщиках находятся в файле `banking_data.csv`:

* `children` — количество детей в семье


* `days_employed` — общий трудовой стаж в днях


* `dob_years` — возраст


* `education` — уровень образования клиента


* `education_id` — идентификатор уровня образования


* `family_status` — семейное положение


* `family_status_id` — идентификатор семейного положения


* `gender` — пол клиента


* `income_type` — тип занятости


* `debt` — имел ли задолженность по возврату кредита


* `total_income` — ежемесячный доход


* `purpose` — цель получения кредита
