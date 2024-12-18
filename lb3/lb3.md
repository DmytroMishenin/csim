## Комп'ютерні системи імітаційного моделювання
## СПМ-23-3, **Мішенін Дмитро Олександрович**

### Лабораторна робота №**3**. Використання засобів обчислювального интелекту для оптимізації імітаційних моделей

<br>

### Варіант 12, модель у середовищі NetLogo:


- **https://github.com/DmytroMishenin/csim/blob/main/lb1/lb1.md**


<br>

### Налаштування середовища BehaviorSearch:

**Обрана модель**:
<pre>
C:\Program Files\NetLogo 6.4.0\models\Sample Models\Biology\Muscle Development.nlogo
</pre>
**Параметри моделі**:  
<pre>
["days-between-workouts" [1 1 30]]
["hours-of-sleep" 8]
["intensity" [50 1 100]]
["lift?" true false]
["%-slow-twitch-fibers" [0 1 100]]

</pre>
Використовувана **міра**:  
Для фітнес-функції  було обрано **кількість анаболічних гормонів**, вираз для розрахунку взято з налаштувань графіка аналізованої імітаційної моделі в середовищі NetLogo  

![Hormones.png](1.png)  

та вказано у параметрі "**Measure**":

<pre>
mean [anabolic-hormone] of patches - mean [catabolic-hormone] of patches
</pre>
Кількість анаболічних гормонів повинна враховуватися **в середньому** за весь період симуляції тривалістю, 300 тактів , починаючи з 0 такту симуляції.  
Параметр зупинки за умовою ("**Stop if**") не використовувався. Значення годин сну встанолено завжди на 8.
Загальний вигляд вкладки налаштувань параметрів моделі:  

![Вкладка налаштувань параметрів моделі](2.png)

**Налаштування цільової функції**:  
Метою підбору параметрів імітаційної моделі, що описує ріст мускулів, є **максимізація** значення анаболічних гормонів – це вказано через параметр "**Goal**" зі значенням **Maximize Fitness**.
Тобто необхідно визначити такі параметри налаштувань моделі, у яких кількість анаболітичних гормонів є максимальною. При цьому цікавить не просто значення у якийсь окремий момент симуляції, а середнє значення за всю симуляцію. Для цього у параметрі "**Collected measure**", що визначає спосіб обліку значень обраного показника, вказано **MAEN_ACROSS_STEPS**. Симуляція буде виконуватись всього 1 раз.
Загальний вигляд вкладки налаштувань цільової функції:  

![Вкладка налаштувань цільової функції](3.png)

**Налаштування алгоритму пошуку** (вкладка Search Algorithm):  
Загальний вид вкладки налаштувань алгоритму пошуку:  

![Вкладка налаштувань пошуку](4.png)

<br>

### Результати використання BehaviorSearch:
Діалогове вікно запуску пошуку:  
![Вікно запуску пошуку](5.png)
Результат пошуку параметрів імітаційної моделі, використовуючи **генетичний алгоритм**:  
![Результати пошуку за допомогою ГА](6.png)
Результат пошуку параметрів імітаційної моделі, використовуючи **випадковий пошук**:  
![Результати випадкового пошуку](7.png)

Випадковий пошук показав себе набагато краще і видав результат, коли м'ясова маса неймовірно висока. Звісно це було досягнуто за допомогою максимізації анаболітичного гормону:

![Результати](8.png)
**Висновок**
У ході виконання лабораторної роботи було досліджено можливості оптимізації імітаційної моделі росту м’язової маси за допомогою засобів обчислювального інтелекту. Для налаштування параметрів моделі, створеної в середовищі NetLogo, було застосовано середовище BehaviorSearch із використанням двох алгоритмів пошуку — генетичного алгоритму та випадкового пошуку.


**Вибір метрики та цільової функції:**
Було обрано метрику, яка враховує різницю між середніми значеннями анаболічних і катаболічних гормонів протягом симуляції. Це дозволило визначити середній рівень ефективності моделі для тривалого періоду часу.
Аналіз ефективності алгоритмів пошуку:
Генетичний алгоритм показав стабільні результати, але виявився менш ефективним за швидкістю пошуку оптимальних параметрів у порівнянні з випадковим пошуком.
Випадковий пошук зміг знайти параметри, що забезпечують значно вищий рівень анаболічних гормонів, однак реалістичність отриманих результатів потребує додаткової перевірки.
Вплив параметрів моделі:
Найбільший вплив на результат оптимізації мали параметри інтенсивності тренувань (intensity) та частоти відпочинку між тренуваннями (days-between-workouts), що свідчить про критичність правильного балансу між навантаженням та відновленням.
