# Вывод find
~~~
gao@fedora:~$ find / -perm -4000 -type f 2>/dev/null
/home/gao/demobash
/usr/bin/at
/usr/bin/chage
/usr/bin/chfn
/usr/bin/chsh
/usr/bin/crontab
/usr/bin/fusermount
/usr/bin/fusermount-glusterfs
/usr/bin/fusermount3
/usr/bin/gpasswd
/usr/bin/grub2-set-bootflag
/usr/bin/mount
/usr/bin/mount.nfs
/usr/bin/newgrp
/usr/bin/pam_timestamp_check
/usr/bin/passwd
/usr/bin/pkexec
/usr/bin/su
/usr/bin/sudo
/usr/bin/umount
/usr/bin/unix_chkpwd
/usr/bin/userhelper
/usr/bin/vmware-user-suid-wrapper
/usr/lib/polkit-1/polkit-agent-helper-1
/usr/libexec/dbus-1/dbus-daemon-launch-helper
/usr/libexec/spice-gtk-x86_64/spice-client-glib-usb-acl-helper
/usr/libexec/libgtop_server2
/usr/libexec/qemu-bridge-helper

~~~

# Почему demobash подозрителен
Sudo и passwd это критически важные, а так же и стандартные системные утилиты, а так как demobash не является стандартной утилитой, и в целом нету утилиты с таким названием, поэтому его и нужно считать подозрительным

# Доказательство student2(root)
~~~
gao@fedora:~$ sudo -u Gao2 ~/demobash -p -c 'whoami; id'
[sudo] пароль для gao: 
root
uid=1001(Gao2) gid=1001(Gao2) euid=0(root) группы=1001(Gao2) контекст=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
~~~

# Как обезвредили 
Удалили право s у владельца(Gao2)
~~~
gao@fedora:~$ sudo chmod -s ~/demobash
gao@fedora:~$ ls -l ~/demobash 
-rwxr-xr-x. 1 root root 1551104 ноя  6 19:08 /home/gao/demobash
~~~

Видим что право s пропало, всё гуд

# Что должен делать администратор проверяя SUID-ы
1. - Автоматизировать проверку аудита
2. - Настроить алерты (оповещения о том что нашлось что то новое и неизвестное)
3. - Контролировать права на запись дерикторий
     



