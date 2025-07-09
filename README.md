# HW-13.1
# 13.1 Уязвимости и атаки на информационные системы

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

### Ответ:
- Какие сетевые службы в ней разрешены?
<img width="368" alt="Задание 1" src="https://github.com/user-attachments/assets/192bfa51-36bb-4a2c-bb4f-78d681c5ea07" />



- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
#### 1. vsftpd 2.3.4: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/17491)
#### 2. UnrealIRCd 3.2.8.1: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/16922)
#### 3. PostgreSQL 8.3.6: [Conversion Encoding Remote Denial of Service](https://www.exploit-db.com/exploits/32849)
#### 4. PostgreSQL 8.3.6: [Low Cost Function Information Disclosure](https://www.exploit-db.com/exploits/32847)

---

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*
### Ответ:
#### Режим SYN.
Отправляется пакет с флагом SYN для установки соединения. Ответ SYN/ACK - порт открыт (После происходит сброс соединения RST). Ответ RST/ACK - порт закрыт.
<img width="557" alt="Задание 2 1" src="https://github.com/user-attachments/assets/4a58b9d7-5d84-4ffc-a2ae-688ef1640f09" />
![Задание 2 2](https://github.com/user-attachments/assets/5f7bc968-6c4f-49e9-a2ff-98f3c3529961)


#### Режим FIN.
Отправляется пакет с флагом FIN. Ответ RST/ACK - порт закрыт. Если ответа нет - порт открыт|фильтруется.
<img width="343" alt="Задание 2 3" src="https://github.com/user-attachments/assets/706b5d14-9452-48cc-8653-7a4197cd999a" />
![Задание 2 4](https://github.com/user-attachments/assets/d9cee609-d2a5-4e34-b01e-a4f3eb0891f1)


#### Режим Xmas.
Отправляется пакет с флагами FIN/PSH/URG. Ответ RST/ACK - порт закрыт. Если ответа нет - порт открыт|фильтруется.
<img width="312" alt="Задание 2 5" src="https://github.com/user-attachments/assets/f7b605b4-dd38-4a59-bf66-17fc60f27fb5" />
![Задание 2 6](https://github.com/user-attachments/assets/295bc6be-bdb1-4c6c-abf7-3cf024ce5f29)


#### Режим UDP.
Отправляет пустой UDP заголовок на каждый порт. Ответ ICMP ошибка о недостижимости порта (тип 3, код 3) - порт закрыт. Другие ICMP ошибки недостижимости - порт фильтруется. После нескольких попыток без ответа - порт  открыт|фильтруется. Ответ UDP - порт открыт.
<img width="294" alt="Задание 2 7" src="https://github.com/user-attachments/assets/71c5bead-0b9e-45cc-a010-bfafeeb22a3a" />
<img width="570" alt="Задание 2 8" src="https://github.com/user-attachments/assets/14b58c39-387b-49a2-9215-9b9c3616af90" />


---
