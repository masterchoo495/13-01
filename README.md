### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.*  

### Решение

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/  
![alt text](https://github.com/masterchoo495/13-01/blob/main/001.png)  

Просканируйте эту виртуальную машину, используя **nmap**  
![alt text](https://github.com/masterchoo495/13-01/blob/main/002.png)  

Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
- LibSSH 0.7.6 / 0.8.4 - Unauthorized Access - https://www.exploit-db.com/exploits/46307
- MySQL / MariaDB - Geometry Query Denial of Service - https://www.exploit-db.com/exploits/38392
- uftpd 2.10 - Directory Traversal (Authenticated) - https://www.exploit-db.com/exploits/51000

---

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

### Решение

С точки зрения сетевого трафика перечисленные режимы отличаются флагами в заголовках (это видно на приложенных ниже снимках из Wireshark).

**SYN**  
В этом режиме на наш SYN запрос сервер отвечает флагом ACK и это означает, что порт открыт/прослушивается.  
![alt text](https://github.com/masterchoo495/13-01/blob/main/syn2.png)  

**FIN**
В этом режиме сканирующим хостом направляются пакеты с FIN флагами (завершение соединения). Сканируемый хост отвечает RST флагом для сброса соединения и это означает, что порт открыт/прослушивается.  
![alt text](https://github.com/masterchoo495/13-01/blob/main/fin2.png)  

**XMAS**  
В этом режиме сканирующим хостом направляются пакеты с флагами PSH, URG и FIN. Результат может вернуть три состояния порта:
- Open-filtered — невозможно определить, открыт порт или отфильтрован. Даже если порт открыт, сканирование Xmas сообщит о нём как open-filtered. Это происходит, когда не получен ответ (даже после повторной передачи)
- Closed — если в ответ приходит сообщение RST
- Filtered — брандмауэр фильтрует сканируемые порты. Это происходит, когда ответом является ошибка ICMP unreachable
![alt text](https://github.com/masterchoo495/13-01/blob/main/xmas2.png)  

**UDP**  
В этом режиме сканирующий хост отправляет UDP пакеты на сканируемый сервер. Если порт закрыт, то от сканируемого хоста поступит ICMP-пакет с содержимым вида "Destination unreachable (Port unreachable)". Если же ответа нет, то порт считается открытым.  
![alt text](https://github.com/masterchoo495/13-01/blob/main/udp.png)  
