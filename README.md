# Язык [EBNF](lang/EBNF.md) + особенности синтаксиса 1 и 2

## Синтаксис языка

Грамматика записанная на нашем языке имеет следующий вид: в одной или нескольких строчках записано правило вида: A = B, где A - идентификатор(название правила), а B - выражение, соответствующая правилам РБНФ комбинация терминальных и нетерминальных символов и специальных знаков.

Могут встречаться следующие операторы:

 * {A} - 0 или больше повторений агрумента A
 * \[A\] - опциональный оператор (0 или 1 вхождение аргумента A)
 * A,B - конкатенация двух аргументов
 * A|B - альтернатива(либо A либо B)
 * (A) - скобки для группировки
 
Аргументами данных операторов могут быть терминалы в одинарных кавычках или выражения. Если в имени терминала или нетерминала присутствует зарезервированный символ его нужно экранировать обратной косой чертой.

Если пользователь хочет записать правило в нескольких строках, то на каждой новой строке, в которой продолжается правило, запись начинается с отступа в 4 пробельных символа. Перенос возможен либо после запятой либо после оператора ИЛИ.

Язык поддерживает многострочные вложенные комментарии, которые начинаются на /* и заканчиваются */.

### Примеры программ:

```
A=(B|C),['aaa']
B='aaa'|'bbb'
C='\{\}'
```

```
A=['a'],{'b'}
   ,['c']
```

## Синтаксический анализатор

```
python3 ebnf.py
```

## Поддержка в среде разработки
Написано расширение для поддержки языка в VSCode.

* Подсветка терминалов, нетерминалов, операторов
* Автодополнение операторов, которые представляют собой парные символы(скобки, кавычки)
* Подсветка кода обернутого скобками или кавычками при наведении курсора

