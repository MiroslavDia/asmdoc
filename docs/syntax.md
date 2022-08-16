# Синтаксис

Синтаксисов языка ассемблера очень много, как и видов ассемблеров, но мы предичитаем синтаксис NASM, ведь он:
* простой
* лексически прост
* и кроссплатформменый

Инструкции языка ассемблера записаны так:
```asm
<инструкция> <аргументы, разделенные через запятую>
```

Пример:

Для GAS Intel:
```gas
add %eax, 4 # В Intel комментарии начинаются с # или //
```

Для GAS ARM:
```gasarm
ADDRQ R7, #4 @ В ARM комментарии начинаются с @ или заключаются в /* */
```
Для NASM:
```nasm
add eax, 4 ; В NASM комментарии начинаются с ;
```
Данная строка добавит 4 ко регистру EAX.