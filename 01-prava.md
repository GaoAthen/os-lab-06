# stat
~~~
[1]
gao@fedora:~$ stat -c '%A %a %n' file1
-rw-r----- 640 file1
[2]
gao@fedora:~$ stat -c '%A %a %n' file1
-rwxr-xr-x 755 file1
[3]
gao@fedora:~$ stat -c '%A %a %n' dir1
drwxr-x--- 750 dir1

~~~

# Таблица перевода

| Буквенно | Восьмерично |
| --- | --- |
| rw-r--r-- | 644 |
|rwxr-x--- | 750 |
|rw------- | 600 |
|r-xr-xr-x | 555 |
