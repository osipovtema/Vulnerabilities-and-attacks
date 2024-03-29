# Домашнее задание к занятию "`Уязвимости и атаки на информационные системы`"



### Задание 1
Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

    Какие сетевые службы в ней разрешены?
    Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

Приведите ответ в свободной форме.

### Решение.

1 - Разрешенные сетевые службы:
- 21/tcp   open  ftp
- 22/tcp   open  ssh
- 23/tcp   open  telnet
- 25/tcp   open  smtp
- 53/tcp   open  domain
- 80/tcp   open  http
- 111/tcp  open  rpcbind
- 139/tcp  open  netbios-ssn
- 445/tcp  open  microsoft-ds
- 512/tcp  open  exec
- 513/tcp  open  login
- 514/tcp  open  shell
- 1099/tcp open  rmiregistry
- 1524/tcp open  ingreslock
- 2049/tcp open  nfs
- 2121/tcp open  ccproxy-ftp
- 3306/tcp open  mysql
- 5432/tcp open  postgresql
- 5900/tcp open  vnc
- 6000/tcp open  X11
- 6667/tcp open  irc
- 8009/tcp open  ajp13
- 8180/tcp open  unknown

2 - Уязвимости:
- vsftpd 2.3.4 - https://www.exploit-db.com/exploits/49757
- GNU Classpath grmiregistry - https://www.exploit-db.com/exploits/32674
- ProFTPD 1.3.1 - https://www.exploit-db.com/exploits/32798


---

### Задание 2
Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

    Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
    Как отвечает сервер?

Приведите ответ в свободной форме.


### Решение.

SYN: 
- Nmap отправляет пакеты SYN на каждый порт, который нужно проверить. 
- Если порт открыт, то сканируемый хост отправляет ответное сообщение SYN-ACK. В этом случае, Nmap знает, что порт открыт и записывает его в список открытых портов. 
- Если порт закрыт, то удаленный хост отправляет сообщение RST.

FIN:
- Nmap отправляет пакеты TCP с установленным флагом FIN на каждый порт, который нужно проверить. 
- Если порт открыт, то сканируемый хост не отправляет ответное сообщение. 
- Если порт закрыт, то сканируемый хост отправляет сообщение RST.

Xmas:
- Nmap отправляет пакеты TCP с установленными флагами FIN, PSH и URG на каждый порт, который нужно проверить. 
- Если порт открыт, то сканируемый хост не отправляет ответное сообщение. 
- Если порт закрыт, то сканируемый хост отправляет сообщение RST ASK.

UDP:
- Nmap отправляет пакеты UDP на каждый порт, который нужно проверить. 
- Если порт открыт, то сканируемый хост не отправляет ответное сообщение. 
- Если порт закрыт, то сканируемый хост отправляет ICMP сообщение типа Port Unreachable. 
UDP сканирование оказалось самым медленным.

---






