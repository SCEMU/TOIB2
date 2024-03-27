
# TOIB-2 
# Отчет по зданию №2 "Идентификация и аутентификация"
Задача 
1. Создать виртуальную машину на базе ОС Debian 12 https://www.virtualbox.org/wiki/Downloads
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.1.0-amd64-netinst.iso
2. Создать пользователя super-{ФИО}, наделить его привилегиями суперпользователя
3. Зайти под созданным пользователем и создать группу group-{группа}
4. Добавить пользователя super-{ФИО} в группу group-{группа}
5. Продемонстрировать наличие пользователя в группе
6. Создать пользователя user-{ФИО}, добавить его в группу group-{группа}
7. Наделить полномочиями (с использованием механизмов дискреционного управления
доступом chmod) пользователя user-{ФИО} по созданию и удалению файлов в домашнем
каталоге пользователя super-{ФИО}
8. Продемонстрировать работу механизмов разграничения доступа.
# Шаги выполнения 
1 Шаг 
![Снимок4](https://github.com/SCEMU/TOIB2/assets/71563287/339a3327-20a0-4fdf-9048-7bab897061ab)



2 Шаг
![Снимок1](https://github.com/SCEMU/TOIB2/assets/71563287/f3035393-8e68-4070-bd0f-93f4423f5b9c)

nikita@debian:~$ su

Пароль: 

root@debian:/home/nikita# sudo useradd super-{SidorenkovND}

root@debian:/home/nikita# passwd super-{SidorenkovND}

Новый пароль:

Повторите ввод нового пароля: 

passwd: пароль успешно обновлён

root@debian:/home/nikita# sudo usermod -aG sudo super-{SidorenkovND}


3 Шаг

root@debian:/home/nikita# sudo groupadd group-{1}


4 Шаг

root@debian:/home/nikita# sudo usermod -aG group-{1} super-{SidorenkovND}
![Снимок2](https://github.com/SCEMU/TOIB2/assets/71563287/8d4ba685-cf9a-4c13-89ad-c23754429309)

5 Шаг

root@debian:/home/nikita# id super-{SidorenkovND}

uid=1002(super-{SidorenkovND}) gid=1002(super-{SidorenkovND}) группы=1002(super-{SidorenkovND
}),27(sudo), 1003(group-{1})




6 Шаг

root@debian:/home/nikita# sudo adduser user_oleg

root@debian:/home/nikita# sudo usermod -aG group-{1} user_oleg

root@debian:/home/nikita# id user_oleg

uid=1004(user_oleg) gid=1004(user_oleg) группы=1004(user_oleg),100(users),1003(group
-{1})





7 Шаг

root@debian:/home/nikita# sudo mkdir /home/super-{SidorenkovND}

root@debian:/home/nikita# chmod 770 /home/super-{SidorenkovND}

root@debian:/home/nikita# chown super-{SidorenkovND}:group-{1234} /home/super-{SidorenkovND}



8 Шаг

root@debian:/home/nikita# su user_nikita

user_nikita@debian:/home/nikita$ touch /home/super-{SidorenkovND}/test_file.txt

user_nikita@debian:/home/nikita$ rm /home/super-{SidorenkovND}/test_file.txt



user_nikita@debian:/home/nikita$ cd /home/super-{SidorenkovND}

user_nikita@debian:/home/super-{SidorenkovND}$ touch test_file.txt

user_nikita@debian:/home/super-{SidorenkovND}$ ls

test_file.txt

![Снимок3](https://github.com/SCEMU/TOIB2/assets/71563287/f74256bd-a446-4d57-b8e7-e41ba0af4955)

