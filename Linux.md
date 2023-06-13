## Part 1. Установка ОС

Версия Ubuntu

![Version](screenshots/Version.png)

## Part 2. Создание пользователя

Создание пользователя и добавление его в группу adm.

![Create](screenshots/Create.png)

cat /etc/passwd

![Etc-passwd](screenshots/Etc-passwd.png)

## Part 3. Настройка сети ОС

Задаем название машины cityorde-1

![Hostname](screenshots/Hostname.png)

И проверяем его

![Hostname-2](screenshots/Hostname-2.png)

Установливаем временную зону, соответствующую текущему местоположению

![Time](screenshots/Time.png)

Выводим названия сетевых интерфейсов с помощью консольной команды

![Names-int](screenshots/Names-int.png)

#### lo (loopback device) – виртуальный интерфейс, присутствующий по умолчанию в любом Linux. Он используется для отладки сетевых программ и запуска серверных приложений на локальной машине.

Получаем ip адрес устройства

![DHCP](screenshots/DHCP.png)

#### DHCP (англ. Dynamic Host Configuration Protocol — протокол динамической настройки узла) — прикладной протокол, позволяющий сетевым устройствам автоматически получать IP-адрес и другие параметры, необходимые для работы в сети TCP/IP. Данный протокол работает по модели «клиент-сервер». Для автоматической конфигурации компьютер-клиент на этапе конфигурации сетевого устройства обращается к так называемому серверу DHCP и получает от него нужные параметры. Сетевой администратор может задать диапазон адресов, распределяемых сервером среди компьютеров. Это позволяет избежать ручной настройки компьютеров сети и уменьшает количество ошибок. Протокол DHCP используется в большинстве сетей TCP/IP.

Выводим на экран внешний ip-адрес шлюза (inet)

![Ip-show](screenshots/Ip-show.png)

Выводим внутренний IP-адрес шлюза (default)

![Ip](screenshots/Ip.png)

Задаем статичные настройки ip, gw, dnsб используя публичные DNS серверы

![Static-ip](screenshots/Static-ip.png)

Применяем внесенные настройки

![Netplan-apply](screenshots/Netplan-apply.png)

Перезагружаем виртуальную машину, проверяем сетевые настройки, пингуем 1.1.1.1 и ya.ru

![Packet-loss](screenshots/Packet-loss.png)

## Part 4. Обновление ОС

Обновляем системные пакеты до последней версии. Повторно вводим команду - появляется сообщение об отсутствии обновлений

![Upgrade](screenshots/Upgrade.png)

## Part 5. Использование команды sudo

##### sudo (англ. Substitute User and do, дословно «подменить пользователя и выполнить») — программа для системного администрирования UNIX-систем, позволяющая делегировать те или иные привилегированные ресурсы пользователям с ведением протокола работы. Основная идея — дать пользователям как можно меньше прав, при этом достаточных для решения поставленных задач.

##### Команда sudo предоставляет возможность пользователям выполнять команды от имени суперпользователя root, либо других пользователей. Правила, используемые sudo для принятия решения о предоставлении доступа, находятся в файле /etc/sudoers.

Разрешаем пользователю, созданному в Part 2, выполнять команду sudo и меняем hostname от его имени

![Sudo](screenshots/Sudo.png)

## Part 6. Установка и настройка службы времени

Настраиваем службы автоматической синхронизации времениб выводим время часового пояса и команду timedatectl show

![NTP](screenshots/NTP.png)

## Part 7. Установка и использование текстовых редакторов

##### Сохранение файлов

Vim. Для выхода с сохранением "esc :wq"

![Vim-create](screenshots/Vim-create.png)

Nano. Для выхода с сохранением "Ctrl+O Ctrl+X"

![Nano-create](screenshots/Nano-create.png)

Mcedit. Для выхода с сохранением "Option+2 Option+0"

![Mcedit-create](screenshots/Mcedit-create.png)

##### Редактирование без изменений

Vim. Для выхода без сохранения "esc :q!"

![Vim-edit](screenshots/Vim-edit.png)

Nano. Для выхода без сохранения "Ctrl+X n"

![Nano-edit](screenshots/Nano-edit.png)

Vim. Для выхода без сохранения "Option+0 No"

![Mcedit-edit](screenshots/Mcedit-edit.png)

##### Поиск по содержимому

Vim. Для поиска "/"

![Vim-seach](screenshots/Vim-seach.png)

Nano. Для поиска "Ctrl+W"

![Nano-seach](screenshots/Nano-seach.png)

Mcedit. Для поиска "Option+7 Find All"

![Mcedit-seach](screenshots/Mcedit-seach.png)

##### Замена содержимого

Vim. Для замены ":%s/что меняем/на что меням/g"
(/g для замены всех вхождений)

![Vim-replace](screenshots/Vim-replace.png)

Nano. Для замены "Ctrl+\ Искомое Замена Параметр (A - заменить все вхождения)"

![Nano-replace](screenshots/Nano-replace.png)

Mcedit. Для замены "Option+4 Искомое Замена Параметр (All - заменить все вхождения"

![Mcedit-replace](screenshots/Mcedit-replace.png)

## Part 8. Установка и базовая настройка сервиса SSHD

Устанавливаем службу SSHd и проверяем ее статус

![Ssh-install](screenshots/Ssh-install.png)

Добавляем автостарт службы при загрузке системы

![Ssh-auto](screenshots/Ssh-auto.png)

Перенастраиваем службу SSHd на порт 2022 (важно раскомментить строку)

![Ssh-port](screenshots/Ssh-port.png)

Команда ps выводит список текущих процессов на вашем сервере, а опция -e показывает все процессы.
Утилита grep помогает фильтровать результаты из команды ps.

![Ssh-ps](screenshots/Ssh-ps.png)

Выполняем команду netstat -tan

netstat выводит состояние TCP-соединений (как входящих, так и исходящих), таблицы маршрутизации, число сетевых интерфейсов и сетевую статистику по протоколам

-tan позволяет отображать все соединения, связанные с TCP

Мы видим протокол, размер очередей приема и получения (в байтах), локальный адрес, удаленный адрес (запись 0.0.0.0:* обозначает «любой IPv4 адрес с любого порта»), а также внутреннее состояние протокола.

![Ssh-netstat](screenshots/Ssh-netstat.png)

## Part 9. Установка и использование утилит top, htop

Запускаем утилиту top

![Top](screenshots/Top.png)

uptime - 26 минут

Количество авторизованных пользователей - 2

Общая загрузку системы - 0.04, 0.01, 0.00

Общее количество процессов - 101

Загрузка cpu - 0.0%

Загрузка памяти - 1976.0 / 1738.0

pid процесса занимающего больше всего памяти - 650

pid процесса, занимающего больше всего процессорного времени - 952


Запускаем улититу htop

Сортируем по PID

![Sort-PID](screenshots/Sort-PID.png)

Сортируем по PERCENT_CPU

![Sort-CPU](screenshots/Sort-CPU.png)

Сортируем по PERCENT_MEM

![Sort- MEM](screenshots/Sort-MEM.png)

Сортируем по TIME

![Sort-TIME](screenshots/Sort-TIME.png)

Отфильтровываем по процессу sshd

![Filter-sshd](screenshots/Filter-sshd.png)

Ищем процесс syslog

![Search-syslog](screenshots/Search-syslog.png)

Добавляем вывод hostname, clock и uptime

![Setup-clock](screenshots/Setup-clock.png)

## Part 10. Использование утилиты fdisk

Получаем информацию о жестком диске, запустив команду sudo fdisk -l

![Fdisk](screenshots/Fdisk.png)

Название жесткого диска - dev/sda

Размер жесткого диска - 10ГБ

Количество секторов - 20971520

Размер swap - 907МБ

## Part 11. Использование утилиты df

Запускаем команду df

![Df](screenshots/Df.png)

Размер раздела - 9299276

Размер занятого пространства - 5176884

Размер свободного пространства - 3628416

Процент использования - 59%


Единица измерения в выводе - килобайты

Запускаем команду df -Th

![Df-Th](screenshots/Df-Th.png)

Размер раздела - 8.9ГБ

Размер занятого пространства - 5.0ГБ

Размер свободного пространства - 3.5ГБ

Процент использования - 59%


Тип файловой системы корневого раздела - ext4

## Part 12. Использование утилиты du

Запускаем команду du и выводим в байтах размер папок

/home

![Du-home](screenshots/Du-home.png)

/var

![Du-var](screenshots/Du-var.png)

/var/log

![Du-varlog](screenshots/Du-varlog.png)


Выводим размер всего содержимого в /var/log (не общее, а каждого вложенного элемента, используя *)

![Du-all](screenshots/Du-all.png)

## Part 13. Установка и использование утилиты ncdu

Устанавливаем утилиту ncdu и выводим размер папок

/home

![Ncdu-home](screenshots/Ncdu-home.png)

/var

![Ncdu-var](screenshots/Ncdu-var.png)

/var/log

![Ncdu-varlog](screenshots/Ncdu-varlog.png)

## Part 14. Работа с системными журналами

Открываем для просмотра /var/log/dmesg, /var/log/syslog, /var/log/auth.log

Время последней успешной авторизации - 13:38:35

Имя пользователя - cityorde-1

Метод входа в систему - login


Перезапускаем службу SSHd

Ищем сообщение о рестарте службы в /var/log/syslog

![Ssh-restart](screenshots/Ssh-restart.png)

## Part 15. Использование планировщика заданий CRON

Используя планировщик заданий, запускаем команду uptime через каждые 2 минуты

![Cron-uptime](screenshots/Cron-uptime.png)

Находим в системных журналах строчки о выполнении

![Cron-time](screenshots/Cron-time.png)

Выводим на экран список текущих заданий для CRON

![Cron-task](screenshots/Cron-task.png)

Удаляем все задания из планировщика заданий

![Cron-del](screenshots/Cron-del.png)
