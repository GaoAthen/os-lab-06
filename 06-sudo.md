# Что может student2
~~~
gao@fedora:~$ sudo -u student2 sudo -l
Соответствие записей Defaults для student2 на fedora:
    !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin, env_reset, env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS", env_keep+="MAIL QTDIR USERNAME
    LANG LC_ADDRESS LC_CTYPE", env_keep+="LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES", env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE",
    env_keep+="LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY", secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/var/lib/snapd/snap/bin

Пользователь student2 может выполнять следующие команды на fedora:
    (ALL) NOPASSWD: /usr/bin/systemctl restart cron
~~~

# Результаты проверки
~~~
gao@fedora:~$ sudo -u student2 sudo systemctl restart cron
Failed to restart cron.service: Unit cron.service not found.
не пропустило

gao@fedora:~$ sudo -u student2 sudo systemctl restart ssh
Извините, пользователю student2 не разрешено выполнять «/usr/sbin/systemctl restart ssh» как root на fedora.
а тут норм
~~~

# Почему visudo безопаснее
Прямое редактирование /etc/sudoers очень опасно, если допустить любую опечатку, лишний пробел и всякое такое, команда sudo будет заблокирована для всех

# почему давать пользователю sudo на vim, less или find опасно?
каждая из этих утилит позволяет выполнить произвольные команды от имени суперпользователя, что приводит к полному захвату контроля над системой
