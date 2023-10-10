## Содержимое

1. Плейбук для clickhouse
2. Плейбук для vector

### Плейбук clickhouse

### 1. Переменные плейбука

- clickhouse_version(задает устанавливаему версию clickhouse)
- clickhouse_packages (задает устанавливаемые пакеты clickhouse)
- clickhouse_dest ( папка для установки инсталляционных пакетов clickhouse)

### 2. Описание работы плейбука

- устанавливаются обязательные пакеты: apt-transport-https, ca-certificates, dirmngr
- устанавливается ключ для подключения к официальному хранилищу clickhouse для скачивания дистрибутивув clickhouse-server и clickhouse-client
- устанавливается официальный репозиторий clickhouse
- происходит установка пакетов clickhouse-server и clickhouse-client
- по окончании установки происходит запуск сервера clickhouse
- создается БД **logs**, если она еще не существует


### Плейбук для vector

### 1. Переменные плейбука

- vector_hostname (задает ip-адрес по которому будет доступен api vector. По умолчанию 127.0.0.1)
- vector_port (задает порт на котором будет доступен api vector. По умолчанию 8686)
- vector_dest ( папка для установки инсталляционных пакетов vector)

### 2. Описание работы плайбука 

- Скачивает конфигурационный **[скрипт](https://repositories.timber.io/public/vector/cfg/setup/bash.deb.sh)**
- Запускает конфигурационный скрипт. Скрипт прописывает репозиторий с официальным дистрибутивом vector.
- Устанавливает **vector** из репозитория командой **apt install vector**, предварительно выполнив **apt update**
- На основе **[jinja2 шаблона](vector/vector.j2)** генерируется рабочую конфигурацию vector 


