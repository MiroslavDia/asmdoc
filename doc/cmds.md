# Команды
### mov <операнд1>, <операнд2>
Переместить регистр <операнд1> в регистр <операнд2>

![Регистры](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Table_of_x86_Registers_svg.svg/1920px-Table_of_x86_Registers_svg.svg.png)

### cmp <операнд1>, <операнд2>
Сравнить <операнд1> с <операндом2>


Примеры:

#### Пример №1

Си:
```c
if(x >= y)
  print("X >= y");
```

Ассемблер:
```nasm
; (переменные x и y находятся в регистрах cx и dx)
cmp cx, dx
jge action
action:
  mov si, r
  call print
  r db 'X >= y'
```

#### Пример №2

Си:
```c
long factorial(long n) {
  if(n == 0)
    return 1;
  else
    return n * factorial(n - 1);
}
```

Ассемблер:
```nasm
; (переменная n в регистре cx, само число будет в bx)
factorial:
  cmp cx, 0
  je i1
  jne else
  i1:
    mov bx, 1
  else:
    sub cx, 1
    call factorial
    mov ax, cx
    mul cx
    mov bx, ax
```

#### Пример №3

Си:
```c
int multiply(int a, int b) {
  return a * b
}
```

Ассемблер:
```nasm
; (переменные a, b в регистрах ax и bx, само число будет в ax)
multiply:
  mov ax, ax
  mov cx, bx
  mul cx
  mov ax, ax
```
