# Вывод ls -l 
~~~
gao@fedora:~$ ls -l /usr/bin/passwd
-rwsr-xr-x. 1 root root 91424 янв 27  2026 /usr/bin/passwd
   ^
Это SUID
~~~

# Вывод ls -l demobash
~~~
[id]
gao@fedora:~$ id
uid=1000(gao) gid=1000(gao) группы=1000(gao),10(wheel) контекст=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

[ls -l]
gao@fedora:~$ ls -l ~/demobash
-rwsr-xr-x. 1 root root 1551104 ноя  6 19:08 /home/gao/demobash

[внутри]
gao@fedora:~$ ~/demobash -p -c 'id'
uid=1000(gao) gid=1000(gao) euid=0(root) группы=1000(gao),10(wheel) контекст=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
~~~

# euid = 0
`euid=0` - означает что процесс выполняется в данный момент времени с макс. правами пользователя

# passwd 
потому что ядро операционной системы проверяет права доступа по вашему EUID пользователя, который меняется в момент запуска этой программы
