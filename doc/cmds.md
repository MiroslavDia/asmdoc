# Команды
### mov <операнд1>, <операнд2>
Переместить регистр <операнд1> в регистр <операнд2>

![Регистры](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Table_of_x86_Registers_svg.svg/1920px-Table_of_x86_Registers_svg.svg.png)

### cmp <операнд1>, <операнд2>
Сравнить <операнд1> с <операндом2>


Примеры:

#### Пример №1

Си:
```
if(x >= y)
  print("X >= y");
```

Ассемблер:
```
; (переменные x и y находятся в регистрах cx и dx)
cmp cx, dx
jge action
action:
  mov si, r
  call print
  r db 'X >= y'
```
