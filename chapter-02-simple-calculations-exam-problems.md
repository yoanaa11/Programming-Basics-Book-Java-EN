# Chapter 2.2. Simple calculations - Exam Problems

In the previous chapter, we got familiar with the system console and how to work with it – how to **read numbers** from the console and how to **print an output** on the console. We went through the main arithmetical operations and briefly mentioned data types. In this chapter we will practice and consolidate what we have learned so far, by solving a few **more complicated problems**, given .


## Reading Numbers from the Console

Before jumping into the practical problems, we are going to revise the most important aspects of what we have studied in the previous chapter. We will start with reading numbers from the console.

### Reading an Integer

We need to create a variable to store the numbers (for example **`num`**), and to use the standard command to read data from the console in combination with the function **`Integer.parseInt(…)`**, which converts text into number:

```java
int num = Integer.parseInt(scanner.nextLine());
```

### Reading a Floating-Point Number

We read a floating-point number the same way we read an integer, but this time we use the function **`double.parseDouble(…)`**:

```java
double num = Double.parseDouble(scanner.nextLine());
```

## Printing text through formatted specificators (format specifiers)

**Format specifier** is an expression which is going to be replaced with a particular value while printing the output. The method **`System.out.printf(…)`** supports printing a string based on a formatted specificators, where the first argument, which we need to pass, is the formatted string, followed by the number of arguments, equal to the number of specificators.

```java
System.out.printf("You are %s %s, a %d-years old person from %s.",
  firstName, lastName, age, town);
```

## Arithmetic Operators

Let's revise the main arithmetic operators for simple calculations.

### Operator +

```java
int result = 3 + 5; // резултатът е 8
```

### Operator -

```java
int result = 3 - 5; // резултатът е -2
```

### Operator *

```java
int result = 3 * 5; // резултатът е 15
```

### Operator /

```java
int result = 7 / 3; // резултатът е 2 (целочислено деление)
double result2 = 5 / 2.0; // резултатът е 2.5 (дробно деление)
```

## Concatenation

By using the operator **`+`** between string variables (or between a string and a number), we have the so-called concatenation (cobining strings).

```java
String firstName = "Ivan";
String lastName = "Ivanov";
int age = 19;
String str = firstName + " " + lastName + " is " + age + " years old";
// Ivan Ivanov is 19 years old
```

## Exam Problems

Now, after we revised how to make simple calculations and how to read and print numbers from the console, let's move to the tasks. We will solve a few **problems from a SoftUni entrance exam**.

## Problem: Training Lab

**A training lab** has a rectangular size **l** for **w** metres, without columns on the inside. The hall is divided into two parts- left and right, with a hallway - approximately in the middle. In both parts, there are **rows with desks**. In the back of the hall, there is a big **entrance door**. In the front, there is a **department** with podium for the lecturer. A single **working place** occupies **70 x 120 cm** (a table with size 70 x 40 cm + space for a chair with size 70 x 80 cm). **The hallway** width is at least **100 cm**. It is calculated that due to the **entrance door** (which has an opening of 160cm) **exactly one working space is lost**, and due to the **department** (кwhich has size of 160 x 120 cm) are lost exactly **2 working places**. Write a program that reads the size of the training lab as input parameters and calculates the **number of working places in it** at the described location (look at the figure).

### Input Data

Are read from the console **2 numbers**, one per line: **l** (length in meters) and **w** (width in meters).

Constraints: **3 ≤ w ≤ l ≤ 100**.

### Output Data

Print on the console one integer number: **the number of working places** in the training lab.

### Sample Input and Output

| Вход   | Изход | Чертеж |
|---------|-------|--------|
|15<br>8.9  |129  | ![](assets/chapter-2-2-images/01.Training-lab-01.png)       | 
|8.4<br>5.2 |39    | ![](assets/chapter-2-2-images/01.Training-lab-02.png)        |

#### Clarification of the Examples

In the first example, the hall length is 1500 cm. There could be located **12 rows** (12 \* 120 cm = 1440 + 60 cm residue). The hall width is 890 cm. From them 100 cm are for the hallway in the middle. In the rest 790 cm could be located **11 desks per row** (11 \* 70 cm = 770 cm + 20 cm residue). **Number of places = 12 * 11 - 3** = 132 - 3 = **129** (we have 12 rows with 11 working places = 132 minus 3 places for podium and entrance door).

In the second example, the hall length is 840 cm. There could be located **7 rows** (7 \* 120 cm = 840, without residue). The hall width is 520 cm. From them 100 cm are for the hallway in the middle. In the rest 420 cm could be located **6 desks per row** (6 \* 70 cm = 420 cm, without residue). **Number of places = 7 * 6 - 3** = 42 - 3 = **39** (We have 7 rows with 6 working places per row = 42 minus 3 laces for podium and entrance door).

### Hints and Guidelines

Try to solve the problem on your own first. If you do not succeed, go through the hints.

#### Idea for Solution

As with any programming task is **important to build an idea for its solution**, before we start to write code. Let's carefully go through the problem requirements. We have to write a program that calculates the number of working places in a training lab, where the number depends on the hall length and height. We notice that the provided input will be in **meters**, and the information about how much space the working places and hallway take, will be in **centimeters**. To do the calculations, we will use the same measuring units, no matter whether we choose to convert length and height into centimeters or the other data in meters. The first option is used for the presented solution.  

Next, we have to calculate **how many columns and how many rows** with desks will fit. We can calculate the columns by **subtracting the width by the necessary space for the hallway (100 cm)** and **divide the difference by 70 cm** (the length of a working place). We will find the rows by dividing the **length by 120 cm**. In both operations with integer and fractional part can be obtained, **In a variable we should store only the integer part**. In the end, we multiply the number of rows by the number of columns and divide it by 3 (the places which are lost because of the entrance door and podium). This is how we calculate the needed value. 

#### Choosing Data Types

From the example, we see that a real number with whole and fractional part can be given as an input, therefore, it is not appropriate to choose data type **`int`**, This is why we use **`double`**. Choosing data type for the next variables depends on the method we choose to solve the problem. . As with any programming task, this one also has **more than one way to be solved**. Two methods will be shown here. 

#### Solution

It is time to go to the solution. We can divide it into three smaller tasks: 
* **Reading** an input.
* **Doing** the calculations.
* **Printing** the output on the console.

The first thing we have to do is read the input from the console. With **`scanner.nextLine()`** we read the values from the console and with the function **`Double.parseDouble(…)`** we convert the string (text) value into **`double`**. 

![](assets/chapter-2-2-images/01.Training-lab-03.png)

Let’s move to the calculations. The special part here is that after dividing the numbers, we have to store only the integer part the result in a variable. 

<table><tr><td><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td><b>Търсете в Google!</b> Whenever we have an idea how to solve a particular problem, but we do not know how to write it in Java or we are dealing with one that we assume that many other people have had before us, the easiest way to solve it is by looking for information on the Internet.</td>
</tr></table>

In this case, we can try with the following search: *java get whole number part of double*. We find out that, one possible way is to use the method **`Math.floor(…)`**. as it works with data types of type **`double`**, For the number of rows and columns we create variables of the same type.  

![](assets/chapter-2-2-images/01.Training-lab-04.png)

Second variant: As we already know, the operator for division **`/`** operates differently on integers and decimals. **When dividing integer with integer** (for example **`int`**), **the result is also an integer**. Therefore, we can search how to convert the real numbers that we have as values for the height and the width, into integers and then divide them. 

In this case, there could be  **data loss**, after having removed the fractional part, so it is necessary that it is converted **expressly** (explicit typecasting). We use the operator for converting data **`(type)`**, by replacing the word **type** with the needed **тdata type** and place it **before the variable**. More for converting data types you can find out in the book ["Въведение в програмирането с Java", стр. 119-123](http://www.introprogramming.info/intro-java-book/read-online/glava3-operatori-i-izrazi/#_Toc243587227).

![](assets/chapter-2-2-images/01.Training-lab-05.png)

With **`System.out.println(…)`** we print the result on the console.

![](assets/chapter-2-2-images/01.Training-lab-06.png)

### Testing in the Judge System

Test your solution here: [https://judge.softuni.bg/Contests/Practice/Index/650#0](https://judge.softuni.bg/Contests/Practice/Index/650#0).


## Problem: Vegetable Market

A gardener is selling his harvest on the vegetables market. He is selling **vegetables for N levs per kg** andи **fruits for M levs per kg**. Write a program that **дcalculates the earnings of the harvest in Euro** (As we assume that **one euro** is equals to **1.94 лв.**).

### Input Data

They are read from the console **4 numbers**, one per line:
* First line – vegetables price per kilogram – a floating-point number.
* Second line – fruit price per kilogram – a floating-point number.
* Third line – : total kilograms of vegetables – an integer.
* Fourth line – total kilograms of fruits – an integer.

**Constraints**: all numbers will be in the range of **0.00** to **1000.00**.

### Output Data

Print on the console **one floating-point number: the earnings of all fruits and vegetables in Euro**.

### Sample Input and Output

| Вход   | Изход  | Вход    | Изход      |
|-----------|----------|-----------|----------------|
|0.194<br>19.4<br>10<br>10|101 | 1.5<br>2.5<br>10<br>10|20.6185567010309| 

**Clarifications for the first example:**

* Vegetables cost: 0.194 lv. \* 10 kg. = **1.94 lv.**
* Fruits cost: 19.4 lv. \* 10 kg.  = **194 lv.**
* Total: **195.94 lv. = 101 euro**. 


### Hints and Guidelines

First, we will give a few ideas and particular hints for solving the problem, followed by the essential part of the code.

#### Idea for Solution

Let's first go through the problem requirements. In this case, we have to calculate the **total income** from the harvest. It is equal to the **sum of the earnings from the fruits and vegetables**, which we can calculate by multiplying **the price per kilogram by the quantity**. The input is given in leva and the output should be in EUR. It is assumed that 1 Euro equals 1.94lv,therefore, in order to get the wanted **output value, we have to divide the sum by 1.94**.

#### Choosing Data Types

After we have a clear idea of how to solve the task, we can continue with choosing appropriate data types. Let's go through the **input**: we have **two integers** for total kilograms of vegetables and fruits, therefore, the variables we declare to store their values will be of **`int`**. The prices of the fruits and vegetables are said to be **floating-point numbers**, so the variables will be of type **`double`**.

We can also declare two variables to store the income from the fruits and vegetables separately. . As we are multiplying a variable of type **`int`** (total kilograms) with one of type **`double`** (price), the result should also be of type **`double`**. Let's clarify that: generally **operators work with arguments of the same type**. Therefore, in order to multiply values of different data types, we have to convert them into the same type. When there are types of different scopes in one expression, the one with the highest scope is the one the other types are converted to, in this case **`double`**. . As there isn't danger of data loss, **the conversion is implicit** (implicit) and is automatically done by the compiler.  

The **output** should also be a **floating-point number**, this means that the result will be stored in a variable of type **`double`**.

#### Solution 

It is time to get to the solution. We can divide it into three smaller tasks: 
* **Reading** the input.
* **Doing** the calculations.
* **Printing** the output on the console.

In order to read the input, we declare variables, which we have to name carefully, so that they can give us a hint about the values they store. With **`scanner.nextLine()`** we read values from the console and with the functions **`Integer.parseInt(…)`** and **`Double.parseDouble(…)`** we convert the particular string value into **`int`** and **`double`**.

![](assets/chapter-2-2-images/02.Vegetable-market-01.png)

We do the necessary calculations: 

![](assets/chapter-2-2-images/02.Vegetable-market-02.png)

The task does not specify special output format, so we just have to calculate the requested value and print it on the console. As in mathematics and so in programming, division has a priority over addition. However, in this task, first we have to **calculate the sum** of the two input values and then we have to **divide by 1.94**. In order to give priority to addition, we can use brackets. With **`System.out.println(…)`** we print the output on the console.  

![](assets/chapter-2-2-images/02.Vegetable-market-03.png)

### Testing in the Judge System

Test your solution here: [https://judge.softuni.bg/Contests/Practice/Index/650#1](https://judge.softuni.bg/Contests/Practice/Index/650#1).


## Problem: Change Tiles

The tiles on the ground in front of an apartment building need changing. The ground has a **square shape with side of N meters**. The tiles are **wide W meters** and **length L meters**. There is one bench on the ground with **width of "M" meters and length of "O" meters**. The tiles under it do not need to be replaced. Each tile is replaced for **0.2 minutes**.

Write a program that reads the size of the ground, the tiles and the bench from the console, and calculates **how many tiles are needed to** cover the ground and calculates **is the total time for replacing the tiles**.

**Example**: **ground** with size 20 м. mm has area of 400 кв.м. **A bench**, that is 1 м. wide and 2 м. long, has area of 2 кв.м. One **tile** is 5 м. wide and 4 м. long and has area of = 20 кв.м. **The area**, that needs to be covered is **400 - 2 = 398 кв.м.** They are needed **398 / 20 = 19.90 tiles**. The needed **time** is **19.90 * 0.2 = 3.98 minutes.**

### Input Data

They are read from the console **5 numbers**:

* **N – length** of a **side** of the ground within the range of [**1 … 100**].
* **W – width** per **tile** in the range of [**0.1 … 10.00**].
* **L – length** per **tile** in the range of [**0.1 … 10.00**].
* **М – width** of the **bench** in the range of [**0 … 10**].
* **О – length** of the **bench** in the range of [**0 … 10**].

### Output Data

Print on the console **two numbers**: **number of tiles**, needed for the repair, and **the time for placing them**, each on a new line.

## Sample Input and Output

| Вход        | Изход    | Вход    | Изход            |
|---------------|------------|-----------|--------------------|
|20<br>5<br>4<br>1<br>2|19.9<br>3.98| 40<br>0.8<br>0.6<br>3<br>5|3302.08333333333<br>660.416666666667| 

**Explanation of the example:**

* **total area** = 20 \* 20 = 400.
* **area of the bench** = 1 \* 2 = 2.
* **are for replacing** = 400 – 2 = 398.
* **area of the tiles** = 5 \* 4 = 20.
* **needed tiles** = 398 / 20 = 19.9.
* **needed time** = 19.9 \* 0.2 = 3.98.

### Hints and Guidelines

Let's make a draft to clarify the task requirements. It can look the following way:

![](assets/chapter-2-2-images/03.Change-tiles-01.png)

### Idea for Solution

It is required to calculate **the number of tiles**, which have to be placed, as well as the **time**, for replacing them. In order to **calculate the number of tiles**, we have to calculate the **area that needs to be covered**, and to **divide it by the area per tile**. The ground is square, therefore, we find the total area by multiplying its side by its value **`N * N`**. After that, we calculate **the area that the bench takes up**, by multiplying its two sides as well **`M * O`**. After subtracting the area of the bench from the area of the whole ground, we obtain the area that needs to be repaired. 

We calculate the area of a single tile by **multiplying** its two sides with one another - **`W * L`**. As we already saied, now we have to **divide** the area for covering by the area of a single tile. This way, we find the number of necessary tiles which we multiply by **0.2** (the time needed for changing single tile). Now, we have the wanted output. 

### Choosing Data Types

ДThe length of the side of the ground, the width and the length of the bench, will be given as **integer numbers**, therefore, in order to store their values, we can declare **variables of type `int`**. We will be given floating-point numbers for the width and the length of the tiles and this is why we will use **`double`**. The output will be a floating-point number as well, so the variables will be of type **`double`**. 

### Solution

As in the previous tasks, we can divide the solution into three smaller tasks:
* **Reading** the input.
* **Doing** the calculations.
* **Printing** the input on the console.

The first thing we have to do is go through **the input** of the task. It is important to pay attention to the sequence they are given in. With **`scanner.nextLine()`** we read values from the console and with **`Integer.parseInt(…)`** and **`Double.ParseInt(…)`** we convert the particular string value into **`int`** and **`double`**.

![](assets/chapter-2-2-images/03.Change-tiles-02.png)

After we have initialized the variables and have stored the corresponding values in them, we move to the **calculations**. As the values of the variables **`n`**, **`a`** and **`b`**, which we work with, are stored in variables of type **`int`**, we can also declare for the results **variables of the same type**.  

![](assets/chapter-2-2-images/03.Change-tiles-03.png)

The variables **`w`** and  **`h`** are of type **`double`**, therefore, for the **area of a single tile** we create a variable of the same type. Finally **we calculate the values that we have to print** on the console. **The number** of needed **tiles** we get by **dividing the area that needs to be covered by the area of a single tile**. When dividing two numbers, one of which is **floating-point number**, the result is also a **floating-point number**. In order, for the calculations to be correct, we store the result in a variable of type **`double`**. The task does not specify special formatting or rounding of the output, so we just print the values with **`System.out.println(…)`**. 

![](assets/chapter-2-2-images/03.Change-tiles-04.png)

### Testing in the Judge System

Test your solution here: [https://judge.softuni.bg/Contests/Practice/Index/650#2](https://judge.softuni.bg/Contests/Practice/Index/650#2).


## Problem: Money

Some time ago **Pesho bought bitcoins**. He will now go on a trip aroung Europe **and he will need euro**. Besides bitcoins, he has and **Chinese yuan**. Pesho wants **to exchange his money in euro** for the excursion. Write a program, which **calculates how much euro** he can buy depending on the following rates:

* **1 Bitcoin = 1168 leva.**
* **1 Chinese yuan = 0.15 dollars.**
* **1 dollar = 1.76 leva.**
* **1 euro = 1.95 leva.**

The exchange office has **commission fee within 0 to 5 percent from the final sum in Euro**.

### Input Data

Three numbers are read from the console:
* On the first line – **number of Bitcoins**. Integer in the range of [**0 … 20**].
* On the second line – **броят китайски юани**. Floating-point number in the range of [**0.00 … 50 000.00**].
* On the third line – **comission fee**. Floating-point number in the range of [**0.00 … 5.00**].

### Output Data
Print one number on the console - **– the result of the exchange of currencies**. Rounding is not necessary.

### Sample Input and Output

| Вход        | Изход    |Вход        | Изход            | Вход         | Изход            |
|---------------|------------|------------|------------------|--------------|------------------|
|1<br>5<br>5|569.668717948718| 20<br>5678<br>2.4|12442.2442010256|7<br>50200.12<br>3|10659.4701177436|

**Explanation**: 
* 1 Bitcoin = 1168 leva
* 5 yuan = 0.75 dollars.
* •	0.75 dollars = 1.32 leva
* **1168 + 1.32 = 1169.32 leva =599.651282051282 Euro**
* **•	Commission fee:** 5% of 599.651282051282 = **29.9825641025641** 
* **Result**: 599.651282051282 - 29.9825641025641 = **569.668717948718 Euro**

### Hints and Guidelines

Let's first think of the way we can solve the task again, before having started to write code.

#### Idea for Solution

Виждаме, че ще ни бъдат подадени **броят биткойни** и **броят китайски юани**. За **изходната стойност** е указано да бъде в **евро**. В условието са посочени и валутните курсове, с които трябва да работим. Забелязваме, че към евро можем да преобразуваме само сума в лева, следователно трябва **първо да пресметнем цялата сума, която Пешо притежава в лева**, и **след това да изчислим изходната стойност**. 

Тъй като ни е дадена информация за валутния курс на биткойни срещу лева, можем директно да направим това преобразуване. От друга страна, за да получим стойността на **китайските юани в лева**, трябва първо да ги **конвертираме в долари**, а след това **доларите - в лева**. Накрая ще **съберем двете получени стойности** и ще пресметнем на колко евро съответстват. 

Остава последната стъпка: да **пресметнем колко ще бъде комисионната** и да извадим получената сума от общата. Като комисионна ще ни бъде подадено **реално число**, което ще представлява определен **процент от общата сума**. Нека още в началото разделим подаденото число на 100, за да изчислим **процентната му стойност**. Нея ще умножим по сумата в евро, а резултатът ще извадим от същата тази сума. Получената сума ще отпечатаме на конзолата. 

#### Избор на типове данни

**Биткойните** са дадени като **цяло число**, следователно за тяхната стойност може да декларираме **променлива от тип `int`**. Като брой **китайски юани и комисионна** ще получим **реално число**, следователно за тях използваме **`double`**. Тъй като **`double`** e типът данни с по-голям обхват, а **изходът** също ще бъде **реално число**, ще използваме него и за останалите променливи, които създаваме. 

#### Решение

След като сме си изградили идея за решението на задачата и сме избрали структурите от данни, с които ще работим, е време да пристъпим към **писането на код**. Както и в предните задачи, можем да разделим решението на три подзадачи: 
* **Прочитане** на входните данни.
* **Извършване** на изчисленията.
* **Извеждане** на изход на конзолата.

**Декларираме променливите**, които ще използваме, като отново внимаваме да изберем **смислени имена**, които подсказват какво съдържат те. Инициализираме техните стойности: със **`scanner.nextLine()`** четем подадените числа на конзолата и конвертираме въведения от потребителя стринг към **`int`** или **`double`**. 

![](assets/chapter-2-2-images/04.Money-01.png)

Извършваме необходимите изчисления: 

![](assets/chapter-2-2-images/04.Money-02.png)

![](assets/chapter-2-2-images/04.Money-03.png)

Накрая **пресмятаме стойността на комисионната** и я **изваждаме от сумата в евро**. Нека обърнем внимание на начина, по който можем да изпишем това: **`euro -= commission * euro`** e съкратен начин за изписване на **`euro = euro - (commission * euro)`**. В случая използваме **комбиниран оператор за присвояване** **`-=`**, който **изважда стойността от операнда вдясно от този вляво**. Операторът за умножение **`*`** има **по-висок приоритет** от комбинирания оператор, затова изразът **`commission * euro`** се изпълнява първи, след което неговата стойност се изважда. Повече за операторите може да прочетете в книгата ["Въведение в програмирането с Java", (стр. 116)](http://www.introprogramming.info/intro-csharp-book/read-online/glava3-operatori-i-izrazi/#_Toc298863965).

В условието на задачата не е зададено специално форматиране или закръгляне на резултата, следователно трябва просто да изчислим изхода и да го отпечатаме на конзолата. 

![](assets/chapter-2-2-images/04.Money-04.png)

Нека обърнем внимание на нещо, което важи за всички задачи от този тип: разписано по този начин, решението на задачата е доста подробно. Тъй като условието като цяло не е сложно, бихме могли на теория да напишем един голям израз, в който директно след получаване на входните данни да сметнем изходната стойност. Напр., такъв израз би изглеждал ето така: 

![](assets/chapter-2-2-images/04.Money-05.png)

Този код би дал правилен резултат, **но се чете трудно**. Няма да ни е лесно да разберем какво прави и дали съдържа грешки, както и как да поправим някоя такава. По-добра практика е **вместо един сложен израз да напишем няколко прости** и да запишем резултатите от тях в променливи със подходящи имена. Така кодът е ясен и по-лесно променяем. 

## Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/650#3](https://judge.softuni.bg/Contests/Practice/Index/650#3).


## Задача: дневна печалба

Иван е програмист в **американска компания** и работи от вкъщи **средно N дни в месеца**, като изкарва **средно по M долара на ден**. В края на годината Иван **получава бонус**, който е **равен на 2.5 месечни заплати**. От спечеленото през годината му се **удържат 25% данъци**. Напишете програма, която да **пресмята колко е чистата средна печалба** на Иван на ден в лева, тъй като той харчи изкараното в България. Приема се, че в годината има точно **365 дни**. **Курсът на долара** спрямо лева ще **се чете от конзолата**.

### Входни данни

От конзолата се четат **3 числа**: 
* На първия ред – **работни дни в месеца**. Цяло число в интервала [**5 … 30**].
* На втория ред – **изкарани пари на ден**. Реално число в интервала [**10.00 … 2000.00**].
* На третия ред – **курсът на долара спрямо  лева** /1 долар = X лева/. Реално число в интервала [**0.99 … 1.99**].

### Изходни данни

На конзолата **да се отпечата 1 число – средната печалба на ден в лева**. Резултатът да се **форматира до втората цифра след десетичния знак**.

### Примерен вход и изход

| Вход        | Изход          |Вход        | Изход            | Вход         | Изход    |
|---------------|------------------|-------------|------------------|-------------|------------------|
|21<br>75.00<br>1.59|74.61| 15<br>105<br>1.71|80.24|22<br>199.99<br>1.50|196.63|

**Обяснение**:
* **1 месечна заплата** = 21 \* 75 = 1575 долара.
* **Годишен доход** = 1575 \* 12 + 1575 \* 2.5 = 22837.5 долара.
* **Данък** = 25% от 22837.5 = 5709.375 лева.
* **Чист годишен доход** = 17128.125 долара = 27233.71875 лева.
* **Средна печалба на ден** = 27233.71875 / 365 = 74.61 лева.

### Насоки и подсказки

Първо да анализираме задачата и да измислим как да я решим. След това ще изберем типовете данни и накрая ще напишем кода на решението.

#### Идея за решение

Нека първо пресметнем **колко е месечната заплата** на Иван. Това ще направим като **умножим работните дни в месеца по парите**, които той печели на ден. **Умножаваме получения резултат** първо по 12, за да изчислим колко е заплатата му за 12 месеца, а след това и **по 2.5**, за да пресметнем бонуса. Като съберем двете получени стойности, ще изчислим **общия му годишен доход**. От него **трябва да извадим 25%**. Това може да направим като умножим общия доход по **0.25** и извадим резултата от него. Спрямо дадения ни курс **преобразуваме доларите в лева**, след което **разделяме резултата на дните в годината**, за които приемаме, че са 365.     

#### Избор на типове данни

**Работните дни за месец** са дадени като **цяло число**, следователно за тяхната стойност може да декларираме променлива от **тип `int`**. За **изкараните пари**, както и за **курса на долара спрямо лева**, ще получим **реално число**, следователно за тях използваме **`double`**. Тъй като **`double`** e типът данни с **по-голям обхват**, а за изходната стойност също се изисква **реално число** (с цяла и дробна част), ще използваме него и за останалите променливи, които създаваме. 

#### Решение

Отново: след като имаме идея как да решим задачата и сме помислили за типовете данни, с които ще работим, пристъпваме към **писането на програмата**. Както и в предходните задачи, можем да разделим решението на три подзадачи: 
* **Прочитане на входните данни**.
* **Извършване на изчисленията**.
* **Извеждане на изход** на конзолата.

**Декларираме променливите**, които ще използваме, като отново се стараем да изберем **подходящи имена**. Със **`scanner.nextLine()`** четем подадените числа на конзолата и **преобразуваме** въведения от потребителя стринг към **`int`** или **`double`** с **`Integer/Double.parseInt/Double(…)`**. 

![](assets/chapter-2-2-images/05.Daily-earnings-01.png)

Извършваме изчисленията: 

![](assets/chapter-2-2-images/05.Daily-earnings-02.png)

Бихме могли да напишем израза, с който пресмятаме общия годишен доход, и без скоби. Тъй като умножението е операция с по-висок приоритет от събирането, то ще се извърши първо. Въпреки това **писането на скоби се препоръчва, когато използваме повече оператори**, защото така кодът става **по-лесно четим** и възможността да се допусне грешка е по-малка. 

Накрая остава да изведем резултата на конзолата. Забелязваме, че се **изисква форматиране на числената стойност до втория знак след десетичната точка**. За целта можем да използваме **форматиращи спецификатори**, т.е. място, което ще бъде заместено с конкретна стойност при отпечатването. В Java за **форматиращ низ** се използва `%`, следван от определена буква (спецификатор). Цяло или дробно число можем да форматираме със спецификаторите **F**/**f**, или **D**/**d**. След него следва цяло положително число, което указва броя на знаците след десетичния знак (повече за форматирането може да прочетете в книгата ["Въведение в програмирането с Java" (стр. 137-143)](http://www.introprogramming.info/intro-java-book/read-online/glava4-vhod-i-izhod-ot-konzolata/#_Toc243587243).

Крайният резултат извеждаме така:

![](assets/chapter-2-2-images/05.Daily-earnings-03.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/650#4](https://judge.softuni.bg/Contests/Practice/Index/650#4).
