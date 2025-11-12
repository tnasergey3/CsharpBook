---
layout: default
title: "14.8 Застосування класів StringReader і StringWriter"
---

# 14.8 Застосування класів StringReader і StringWriter

Для виконання операцій введення-виведення з запам'ятовуванням в деяких додатках нях в якості базової пам'яті іноді краще використовувати масив типу string, ніж масив типу byte . Саме для таких випадків і передбачені класи StringReader і StringWriter . Зокрема, клас StringReader успадковує від класу TextReader , а клас StringWriter — від класу TextWriter . Отже, вони представля ють собою потоки, які мають доступ до методів, визначених в цих двох базових класах, що дозволяє, наприклад, викликати метод ReadLine() для об'єкта класу StringReader а метод WriteLine() — для об'єкта класу StringWriter. Нижче наведено конструктор класуStringReader:

StringReader(string s)

де s позначає символьний рядок, з якого проводиться читання. У класі StringWriter визначено кілька конструкторів. Нижче представлено один з найбільш часто використовуваних.

StringWriter()

Цей конструктор створює записуючий потік, який поміщає виводимі дані в рядок. Для отримання вмісту цього рядка достатньо викликати метод ToString(). Нижче наведено приклад, що демонструє застосування класів StringReader і StringWriter.

Лістинг 14.06 - Приклад застосування класів StringReader і StringWriter

class StrRdrWtrDemo

{

static void Main()

{

StringWriter strwtr = null;

StringReader strrdr = null;

try

{

// Створити об'єкт класу StringWriter.

strwtr = new StringWriter();

// Вивести дані в записуючий потік типу StringWriter.

for (int i = 0; i < 10; i++)

strwtr.WriteLine("Значення i дорівнює: " + i);

// Створити об'єкт класу StringReader.

strrdr = new StringReader(strwtr.ToString());

//А тепер ввести дані з читаючого потоку типу StringReader.

string str = strrdr.ReadLine();

while (str != null)

{

str = strrdr.ReadLine();

Console.WriteLine(str);

}

}

catch (IOException exc)

{

Console.WriteLine("Помилка введеннявиведення " + exc.Message);

}

finally

{

// Звільнити ресурси читаючого та записуючого потоків.

if (strrdr != null) strrdr.Close();

if (strwtr != null) strwtr.Close();

}

}

}

У даному прикладі спочатку створюється об'єкт strwtr класу StringWriter , в який виводяться дані за допомогою методу WriteLine() . Потім створюється об'єкт класу StringReader з використанням символьного рядка, що міститься в об'єкті strwtr . Цей рядок отримується в результаті виклику методу ToString()для об'єкта strwtr. І нарешті, вміст цього рядка зчитується за допомогою методу ReadLine().
