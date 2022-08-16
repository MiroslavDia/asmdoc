# Команды
### mov <операнд1>, <операнд2>
Переместить регистр <операнд1> в регистр <операнд2>

![Регистры](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Table_of_x86_Registers_svg.svg/1920px-Table_of_x86_Registers_svg.svg.png)

### cmp <операнд1>, <операнд2>
Сравнить <операнд1> с <операндом2>


# Примеры:

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

# Первые программы

Программы, которые мы будем писать

Для этого нужно


Ядро Linux

Процессор семейства Intel, x86

#### Простая программа, которая выведет текст и вернет код выхода 0 (успех)

hello.asm:
```nasm
section .data
  msg: db 'Hello, world!',0
  len: equ $ - msg
 
section .text ; Секция с кодом
  global _start ; Должно быть для GCC
_start:
  mov eax, 4 ; EAX - регистр с номером функции, 4 - системный вызов SYS_WRITE
  mov ebx, 1 ; EBX - регистр с потоком вывода, 1 - поток STDOUT
  mov ecx, msg ; ECX - регистр с текстом, msg - наше сообщение
  mov edx, len ; EDX - длина текста, len - число с длиной нашего сообщения
  int 0x80 ; INT - прерывание, 0x80 - вызов ядра Linux
  mov eax, 1 ; 1 - системный вызов SYS_EXIT
  mov ebx, 0 ; EBX - код выхода
  int 0x80 ; Можно и 80h, или 0x80, без разницы 80h или 0x80, оно в любом случае будет вызывать ядро Linux
```

Команды:
```bash
$ nasm -f elf -o hello.o hello.asm
$ ld -o hello hello.o
$ ./hello
Hello, world!
```

<br/>
<p align="center">
Навигация:
  
  <div align="left">
    ⇜ <a href="start.md">Прошлая страница</a>
  </div>
  <div align="right">
    ⇝ <a>Следующяя страница</a>
  </div>
</p>

