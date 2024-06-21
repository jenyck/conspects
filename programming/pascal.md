# Pascal

Структура программы:

```pascal
program example;
{comment}
var
    {variables}
    x, y, z: integer;
    {initialisation}
    flag: boolean = true;
begin
    {main program}
end.
```

Команда компилятора, создающая исполняемый файл **hello** и объектный
**hello.o** из файла исходного кода **hello.pas**:

```bash
fpc hello.pas
```

Пример строкового литерала/строковой константы: `'Текстовая строка123№;%:?\*'`

Операторы разделяются точкой с запятой:

```pascal
begin
    writeln('Hello!');
    writeln('Goodbye!')
end.
```

Форматирование вывода чисел типа _float_:

```pascal
writeln(14/7:7:3) {число : количество знакомест : знаков после запятой}
```

Вывод - 3 до запятой + 1 запятая + 3 после = 7 знаков: `$  2.000`

Чтение потока ввода, пока не встретится EOF:

```pascal
begin
    while not EOF do
        readln()
end.
```
