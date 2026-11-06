# Вывод прав при маске (022/077)
~~~
(маска 0022)

gao@fedora:~$ stat -c '%a %n' new_default dir_default
644 new_default - rw-r-r--
755 dir_default - rwxr-xr-x

(маска 0077)

gao@fedora:~$ stat -c '%a %n' new_default dir_default
644 new_default - rw-r-r--
755 dir_default - rwxr-xr-x
[права никак не меняются]
~~~

# Расчёт 666 и 777
`666` - [rw-rw-rw]
`777` - [rwxrwxrwx]
