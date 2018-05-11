[Повернутись](../index.md)
# [](#header-1)Assignment #6. Trees

## Загальне завдання
* Розібратись в загальному і структурою даних "дерево" - де використовується, яому так називається.
* Розібрати всі запропоновані варіанти - виконувати потрібно тільки одне (за варіантом), але теоретичні питання будуть стосуватись всіх завданнь.
* Уважно розібратись з алгоритмічної складністю роботи з деревами (а точніше - звідки там так часто береться логарифм) 



## [](#header-2)Варіант #0. Рендеринг зображення метод трасування променів

## [](#header-2)Варіант #1. Побудова синтаксичного дерева

## [](#header-2)Варіант #2. Пошук найближчих установ до заданої географічної точки.

Майже будь-якій програмі (застосунку, сервісу) сьогодні доводиться мати справу з  даними. Сервіси зберігають інформацію про своїх користувачів (ім'я\логін), їх дії (замовлення, особисті кабінети), купу аналітичних даних (що клікнув користувач, як довго знаходився на певній сторінці, як часто заходить у сервіс). Цих даних накопичується так багато, що обробляти та аналізувати їх вручну стає дуже важко. Виникла ціла галузь комп'ютерних наук - Data Science, термін Bid Data та багато чого іншого цікавого, з чим ви ще обов'язково познайомитесь далі.

В цій же роботі вам пропонується більш просте завдання - написати структуру  для ефективної обробки певних даних. Очевидно, що якщо хранити дані (скажімо, інформацію про користувачів) невпорядковано, то навіть при порівняно невеликій базі в мільйон записів кожна операція - спроба щось знайти буде потребувати повного перебору абсолютно всіх записів, що буде займати багато ресурсів - як процесорних, так і часових.

Будь-яка сучасна база даних підтримує індексування - створення допоміжної структури даних, що дозволяє набагато швидше виконувати певнії дії над даними. Наприклад, якщо побудувати навіть найпростіше бінарне дерево пошуку, то запит "знайти користувача віком 32 роки" буде виконуватись вже за логаріфмичний час. Префіксне дерево в свою чергу дозволить виконувати подібні запити на полях що є рядками (наприклад, ім'я). Сьогоді в базах даних дуже часто біля одного набору даних знаходиться декілька індексів,що дозволяють робити ефективні запити на різних полях.

Індекси можна будувати не тільки над рядками та числами, але й над більш цікавими даними - наприклад над географічними точками. Для цього є навіть окрема назва - Spatial index. Найчастіше,  такий індекс реалізовується за допомогою спеціальних дерев, що називаються R-Tree

Отже, вам дається файл наступного формату (лінк)
Широта, Довгота, Тип, Вулиця, Номер будинку

Ці дані взяті з відкритих джерел - із Open Street Map. Для вашої зручності дані були попередньо оброблені у такий зручний формат із оригінального формату .osm. Ваше завдання - написати програму, що буде приймати на вході географічну точку (широта, довгота), ті ціле число  N. Програма має вивести на еркан всі установи, що потрапляють у квадрат довжиною N кілометрів із центром в заданій точці. Очевидний вариант - перебирати всі точки та перевіряти, чи потрапляє вона в потрібний сектор. Але це дуже нефективно, і суть завдання полягає саме у роботі зі структурою даних.

*Більше складне завдання:* вводити не довжину сторони квадрату, а радіус кола

Також пам'ятайте, що координати  певної точки на планеті - це широта та довгота, при чому відстань у один градус між двома точками на екваторі набагата більше, ніж відстань у один градус близкьо для полюсів. Це треба враховувати і корректно рахувати відстані.  Для кращого розуміння потрібно почитати про Проекцію Меркатора (лінк) та пограти у відому гру від Гугла (лінк), що показує як ця проекція викривлює справжні масштаби