# pam
*** Задача - Запретить всем пользователям, кроме группы admin, логин в выходные (суббота и воскресенье), без учета праздников.

Так как модуль `pam_time` не работает с группами, выполляется следующее:

Добавляется две строки в /etc/pam.d/login

```
account    [success=1 default=ignore] pam_succeed_if.so user ingroup admin
account    required     pam_time.so
```

Далее в файле time.conf запрещается всем входить в систему в выходные дни

>login;*;*;Wk0000-2400

Проверка

>vagrant up

>vagrant ssh

>groupadd admin

>useradd -G admin test1

>useradd test2

Пользователь test1 - будет иметь возможность логиниться в выходные, test2 - только будние дни.
