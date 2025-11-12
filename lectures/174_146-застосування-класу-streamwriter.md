---
layout: default
title: "14.6 Застосування класу StreamWriter"
---

# 14.6 Застосування класу StreamWriter

Для створення символьного потоку виведення достатньо обгорнути об'єкт класу Stream , наприклад FileStream , в оболонку класу StreamWriter . В класі StreamWriter визначено кілька конструкторів. Нижче наведений майже найпоширеніший серед них:

StreamWriter(Stream потік)

де потік означає ім'я відкритого потоку. Цей конструктор генерує виняток ArgumentException , якщо потік не відкритий для виводу, а також виняток ArgumentNullException , якщо потік показується порожнім. Після створення об'єкта класу StreamWriter відбувається автоматичне перетворення символів в байти.

Нижче наведено простий приклад сервісної програми введення з клавіатури та виведення на диск набраних текстових рядків, збережених у файлі test.txt . Введений текст вводиться до тих пір, поки в ньому не зустрінеться рядок " стоп " . Для символьного ви воду в файл у цій програмі використовується об'єкт класу FileStream , упакований у обгортку класу StreamWriter .

Лістинг 14.4 - Приклад StreamWriter

class KtoD

{

static void Main()

{

string str;

FileStream fout;

// Спочатку відкрити потік файлового введеннявиведення.

try

{

fout = new FileStream("test.txt", FileMode.Create);

}

catch (IOException exc)

{

Console.WriteLine("Помилка відкриття файлу: " + exc.Message);

return;

}

// Обгорнути потік файлового введеннявиведення в оболонку класу StreamWriter.

StreamWriter fstr_out = new StreamWriter(fout);

try

{

Console.WriteLine("Введіть текст, а після закінчення - 'стоп'.");

do

{

Console.Write(": ");

str = Console.ReadLine();

if (str != "стоп")

{

str = str + " "; // додати новий рядок fstr_out.

Write(str);

}

} while (str != "стоп");

}

catch (IOException exc)

{

Console.WriteLine("Помилка введеннявиведення: " + exc.Message);

}

finally

{

fstr_out.Close();

}

}

}
