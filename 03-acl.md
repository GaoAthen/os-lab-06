# Вывод getfacl
~~~
gao@fedora:~$ getfacl ~/secret.txt
getfacl: Removing leading '/' from absolute path names
# file: home/gao/secret.txt
# owner: gao
# group: gao
user::rw-
user:Gao2:r--
group::---
mask::r--
other::---
~~~

# Вывод ls -l
~~~
gao@fedora:~$ ls -l ~/secret.txt
-rw-r-----+ 1 gao gao 47 ноя  6 18:09 /home/gao/secret.txt

знак + означает что тут используются расширенные списки контроля доступа
~~~

Для аудитора или офицера ИБ этот символ служит мгновенным сигналом, внимание, здесь действуют нестандартные правила доступа

# Что выдало cat до ACL и после
~~~
[До]
gao@fedora:~$ sudo -u Gao2 cat ~/secret.txt
cat: /home/gao/secret.txt: Отказано в доступе

[После]
gao@fedora:~$ sudo -u Gao2 cat ~/secret.txt 
секретные данные проекта

[Удалил]
gao@fedora:~$ sudo -u Gao2 cat ~/secret.txt
cat: /home/gao/secret.txt: Отказано в доступе
~~~

# Почему ACL удобнее обычного добавление в группу-владельца
*1 -  Защита от избыточных прав, если добавить во владельцев студента, он получит все права
*2 - Избежание конфликта интересов
*3 - Удобство автоматизации
