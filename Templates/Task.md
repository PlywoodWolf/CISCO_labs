### 🗺️ Карта сети
> [!info] Скриншот
> 
> Проект CPT
> 

### 📋 Таблица IP-адресации
| Устройство | Интерфейс / VLAN | IP-адрес     | Маска         | Шлюз        |
| :--------- | :--------------- | :----------- | :------------ | :---------- |
| R1         | Fa0/0            | 192.168.1.1  | 255.255.255.0 | -           |
| PC0        | NIC              | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| ...        | ...              | ...          | ...           | ...         |

### ⚙️ Выполнение работы (Конфигурация)

#### 1. Базовая настройка устройств
> [!example] Команды (R1)
> ```bash
> enable
> configure terminal
> hostname R1
> interface fa0/0
> ip address 192.168.1.1 255.255.255.0
> no shutdown
> ```

#### 2. Настройка [Следующий этап, например VLAN]
> [!example] Команды (SW1)
> ```bash
> vlan 10
> name VLAN10
> interface fa0/1
> switchport mode access
> switchport access vlan 10
> ```

*(Добавляйте столько разделов, сколько этапов в задании)*

### 🔍 Проверка работы

#### 1. Проверка таблиц маршрутизации / коммутации
> [!note] Вывод команды `show ip route` на R1
> ```text
> Gateway of last resort is not set
> C    192.168.1.0/24 is directly connected, FastEthernet0/0
> O    192.168.2.0/24 [110/2] via 192.168.1.2, 00:00:05, FastEthernet0/0
> ```

#### 2. Тестирование связи (Ping / Tracert)
> [!success] Результат ping с PC0 на PC1
> ```text
> Pinging 192.168.2.10 with 32 bytes of data:
> Reply from 192.168.2.10: bytes=32 time<1ms TTL=126
> Reply from 192.168.2.10: bytes=32 time<1ms TTL=126
> ```

#### 3. Проверка работы сервисов (WEB, DNS, DHCP)
> [!info] Скриншот
> (Сюда вставьте скриншот браузера в Packet Tracer или вывода команды `ipconfig /renew`)

---