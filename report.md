# Лабораторная работа №3

### Инструменты
Parallels, Ubuntu Server, Терминал

### Ход работы
**1. Настройка виртуальных машин и проверка доступа в Интернет**

Установлены 3 виртуальные машины с Ubuntu в Parallels:
- Машина A - основной хост
- Машина B - вторая виртуальная машина
- Машина C - третья виртуальная машина

Проверка доступа в Интернет с основного хоста без скачивания страницы:
```bash
wget --spider google.com
```
<img width="455" height="192" alt="image" src="https://github.com/user-attachments/assets/dbe14562-703f-495b-a990-312c6e00a54f" />

**2. Настройка правил доступа**

**2.1. Получение IP-адресов машин**
```bash
# Команда для получения информации о сетевых интерфейсах
ip a
```
<img width="460" height="185" alt="image" src="https://github.com/user-attachments/assets/7c459fbc-555d-4478-a8e2-6d3d1abdf42f" />
<img width="550" height="163" alt="image" src="https://github.com/user-attachments/assets/3811f87d-36f9-42b3-bb03-26036177e6d7" />
<img width="457" height="184" alt="image" src="https://github.com/user-attachments/assets/18e68509-add5-4039-a127-8e2a23e9d7c1" />

Полученные IP-адреса:
- Машина A: 192.168.68.104
- Машина B: 192.168.68.106
- Машина C: 192.168.68.107

**2.2. Блокировка доступа от машины C к машине B:**
```bash
# iptables - утилита настройки фильтрации трафика. С помощью данной команды мы добавляем правило для указанного IP – отбрасывать пакеты
sudo iptables -A INPUT -s 192.168.68.107 -j DROP
```
<img width="575" height="39" alt="image" src="https://github.com/user-attachments/assets/9da6bd68-da44-4eb4-8e42-bd063286841b" />


**2.3. Проверка сетевого взаимодействия**

<img width="1541" height="449" alt="image" src="https://github.com/user-attachments/assets/65f887b9-4113-4051-b892-e951c17190bb" />
<img width="521" height="316" alt="image" src="https://github.com/user-attachments/assets/5b7b8699-3245-4498-9771-8df53d2ec219" />

*Результат: поднято три виртуальные машины, на каждой настроена сеть, а также на машину B добавлены прафила фильтрации с помощью iptables, которые ограничивают трафик между указанными машинами.*

