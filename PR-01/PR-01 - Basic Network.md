---
tags:
  - cisco
  - packet-tracer
  - лабораторная
номер: ПР-01
тема: Простейшая сеть
дата: 2026-11-01
статус: Выполнена
---

#  ПР-01: [Простейшая сеть]

![[PR-01 - Basic Network.pdf]]

## 🎯 Цель работы.
>[Познакомиться с Cisco Packet Tracer и режимом симуляции; смоделировать простейшую сеть.]
___
## Задание 1:

### 🗺️ Карта сети
> [!info]  Скриншот
> ![[Pasted image 20261101173611.png]]
> Проект CPT
> ![[PR-01 - Basic Network.pkt]]
### 📋 Таблица IP-адресации

| Устройство | Интерфейс     | IP-адрес     | Маска         | Шлюз        |
| :--------- | :------------ | :----------- | :------------ | :---------- |
| PC0        | FastEthernet0 | 192.168.1.2  | 255.255.255.0 | -           |
| PC1        | FastEthernet0 | 192.168.1.1  | 255.255.255.0 | -           |

### ⚙️ Выполнение работы (Конфигурация)

#### 1. Базовая настройка PC0
> [!example] Команды (PC0)
> Desktop -> IP Configuration
 ![[Pasted image 20261101080435.png]]


#### 2. Базовая настройка PC1
> [!example] Команды (PC0)
> Desktop -> IP Configuration
![[Pasted image 20261101080610.png]]

### 🔍 Проверка работы

#### 1. Тестирование связи (Ping PC0 -> PC1)
> [!success] Результат ping с PC0 на PC1
> Desktop -> Command Prompt
> ```text
> C:\>ping 192.168.1.1
> 
> Pinging 192.168.1.1 with 32 bytes of data:
> 
> Reply from 192.168.1.1: bytes=32 time<1ms TTL=128
> Reply from 192.168.1.1: bytes=32 time<1ms TTL=128
> Reply from 192.168.1.1: bytes=32 time<1ms TTL=128
> Reply from 192.168.1.1: bytes=32 time<1ms TTL=128
> 
> Ping statistics for 192.168.1.1:
> 	Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
> Approximate round trip times in milli-seconds:
> 	Minimum = 0ms, Maximum = 0ms, Average = 0ms
> ```

> [!info] Результат Ping (PC0 -> PC1)
> ![[Pasted image 20261101065428.png]]
---
## Задание 2:
### 🗺️ Карта сети
> [!info]  Скриншот
> ![[Pasted image 20261101084403.png]]
> Проект CPT
> ![[PR-01 - Basic Network 2.pkt]]

### 📋 Таблица IP-адресации
| Устройство | Интерфейс / VLAN | IP-адрес     | Маска         | Шлюз        |
| :--------- | :--------------- | :----------- | :------------ | :---------- |
| PC0        | FastEthernet0    | 192.168.0.1  | 255.255.255.0 | -           |
| PC1        | FastEthernet0    | 192.168.0.2  | 255.255.255.0 | -           |
| PC2        | FastEthernet0    | 192.168.0.3  | 255.255.255.0 | -           |
| PC3        | FastEthernet0    | 192.168.0.4  | 255.255.255.0 | -           |
| PC4        | FastEthernet0    | 192.168.0.5  | 255.255.255.0 | -           |

---

### ⚙️ Выполнение работы (Конфигурация)

#### 1. Базовая настройка устройств
> [!example] Команды (PC0-3)
>  Desktop -> IP Configuration
> ![[Pasted image 20261101084906.png]]

#### 2. [Симуляция]
> [!example] 
> ```
> Команды (CPT)
> 1.Simulation
> 2.Edit Filters -> снять все фильры кроме icmp
>```
> ![[Pasted image 20261101085822.png]]
> ```
> Команды (PC1)
> 1.Desktop -> Command Prompt
> 2.ping 192.168.0.3
>```
>![[Pasted image 20261101090937.png]]
>```
> Команды (CPT)
> * Capture/Forward либо
> * Auto Capture/Play
>```
>![[Pasted image 20261101090804.png]]
>```
> Команды (CPT)
> - По щелчку на конверте получим информацию об уровнях модели OSI и структуре пакета
>```
> ![[Pasted image 20261101091511.png]]
> ![[Pasted image 20261101091524.png]]

#### 3. Настройка [PC4]
> [!example] Команды (PC4)
> Desktop -> Command Prompt
> ```
> ipconfig 192.168.0.5 255.255.255.0
> ```
> ![[Pasted image 20261101085256.png]]

### 🔍 Проверка работы

#### 1. Проверка настроек (PC0-4)
> [!success] Результат ipconfig на PC0-4
> ```text
> ipconfig
> ```
> ![[Pasted image 20261101092937.png]]

___
## 📝 Вывод
> В ходе выполнения работы я научился...
> * Настраивать базовые параметры устройств (IP и маски)
> * Проверять связь между устройствами

---

## 💡 Шпаргалка по командам (для себя)
> [!tip] Основные команды из этой работы
> * `ipconfig` — статус/настройка интерфейсов
> * `ping` — проверка связи