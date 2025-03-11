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

**syn**
![alt text](https://github.com/masterchoo495/13-01/blob/main/syn.png)  

**fin**
![alt text](https://github.com/masterchoo495/13-01/blob/main/fin.png)  

**xmas**
![alt text](https://github.com/masterchoo495/13-01/blob/main/xmas.png)  

**udp**
![alt text](https://github.com/masterchoo495/13-01/blob/main/udp.png)  
