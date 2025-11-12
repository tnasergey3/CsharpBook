---
layout: default
title: "Лекція 2 — Типи даних, змінні, консольний ввід/вивід"
---

# Розділ 2. Типи даних, поняття змінних, консольний ввід та вивід

## 2.1 Змінна в мові C#
**Змінна** — іменований контейнер для зберігання значень у пам’яті. Має **ім’я**, **тип** і **значення**.

### Ідентифікатори (імена змінних)
- Починаються з літери або `_`; далі — літери/цифри/`_`
- Без пробілів і спецсимволів
- Чутливі до регістру (`myVar` ≠ `myvar`)

**Коректно:** `myVariable`, `counter`, `_privateField`, `CalculateSum`  
**Некоректно:** `123variable`, `my Variable`, `for`

### Приклади (Лістинг 2.1)
```csharp
int age;
age = 30;
string name = "John";
```

### Оператор присвоєння `=` (Лістинг 2.2)
```csharp
int x; x = 5;
string name; name = "John";
double result; result = 10.5;
```

---

## 2.2 Типи даних
- **Прості (значення):** `bool`, `byte/sbyte`, `short/ushort`, `int/uint`, `long/ulong`, `char`, `float`, `double`, `decimal`
- **Посилальні:** класи, масиви, рядки тощо

### Таблиця 2.1 — Прості типи
| Тип | Опис |
|---|---|
| `bool` | Логічний (`true/false`) |
| `byte` | 8-біт без знаку (0–255) |
| `char` | Символ Unicode (16-біт) |
| `decimal` | Десятковий (фінанси) |
| `double` | Подвійна точність |
| `float` | Одинарна точність |
| `int` | 32-біт цілий |
| `long` | 64-біт цілий |
| `short` | 16-біт цілий |
| `uint` | 32-біт без знаку |
| `ulong` | 64-біт без знаку |
| `ushort` | 16-біт без знаку |

### 2.2.1 Цілочисельні типи (Табл. 2.2)
| Тип | Біти | Діапазон |
|---|---:|---|
| `byte` | 8 | 0..255 |
| `sbyte` | 8 | -128..127 |
| `short` | 16 | -32768..32767 |
| `ushort` | 16 | 0..65535 |
| `int` | 32 | −2,147,483,648..2,147,483,647 |
| `uint` | 32 | 0..4,294,967,295 |
| `long` | 64 | −9,223,372,036,854,775,808..9,223,372,036,854,775,807 |
| `ulong` | 64 | 0..18,446,744,073,709,551,615 |

**Лістинг 2.3 — Відстань до Сонця**
```csharp
long miles = 93000000;
long inches = miles * 5280 * 12;
Console.WriteLine("Відстань до Сонця: " + inches + " дюймів.");
```

### 2.2.2 Плаваюча крапка (`float`, `double`)
```csharp
double area = 10.0;
double r = Math.Sqrt(area / 3.1416);
Console.WriteLine($"Радіус = {r}"); // Лістинг 2.5
```

### 2.2.3 `decimal` (фінанси)
```csharp
decimal price = 19.95m, discount = 0.15m;
Console.WriteLine($"Ціна зі знижкою: {(price * (1 - discount)):C}");
```

### 2.2.4 Логічний `bool`
```csharp
bool b = true;
if (b) Console.WriteLine("Виконується.");
Console.WriteLine("10 > 9 дорівнює " + (10 > 9));
```

### 2.2.5 Консольний ввід/вивід і форматування
```csharp
int count = 2, price = 3;
Console.WriteLine($"Ви замовили {count} предмета по ціні ${price} кожен.");
Console.WriteLine("10/3 = {0:#.##}", 10.0/3.0);
Console.WriteLine("{0:###,###.##}", 123456.56);
```

**Ввід з консолі**
```csharp
string s = Console.ReadLine();
int i = int.Parse(Console.ReadLine());
double d = double.Parse(Console.ReadLine());
short sh = short.Parse(Console.ReadLine());
```

### 2.2.6–2.2.9 Літерали, керуючі послідовності, рядки
```csharp
char ch = '\''; // одинарна лапка
Console.WriteLine("Перший рядок\nДругий рядок");
Console.WriteLine(@"Літерaльний рядок
без екранування символів");
```

### 2.2.10 `var` — неявно типізовані
```csharp
var s1 = 4.0; var s2 = 5.0;
var hypot = Math.Sqrt(s1*s1 + s2*s2);
Console.WriteLine($"{hypot:#.###}");
```

### 2.2.12–2.2.16 Перетворення та приведення
```csharp
double x = 10.0, y = 3.0;
int r = (int)(x / y); // явне приведення

byte b1 = 10;
// b1 = b1 * b1; // помилка
b1 = (byte)(b1 * b1); // просування до int → каст до byte
```
