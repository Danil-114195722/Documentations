# Установка Shadowsocks на сервер

### 1. Обновляемся

```shell
apt update && apt upgrade -y
```

### 2. Устанавливаем требуемые пакеты

```shell
apt install shadowsocks-libev -y
```

### 3. Смотрим наш внешний IP-адрес

```shell
ip a
```

### 4. Редактируем конфиг под наши параметры

```shell
vi /etc/shadowsocks-libev/config.json
```

### 5. Перезапускаем службу

```shell
service shadowsocks-libev restart
service shadowsocks-libev status
```

### 6. Добавляем службу а автозагрузку

```shell
systemctl enable shadowsocks-libev
```

### 7. Скачиваем и настраиваем [клиентскую часть][win-client] под Windows

<br><hr>

# Подключаем плагин обфускации V2Ray

### 8. Скачиваем [плагин v2ray][server-v2ray] для VPS сервера

```shell
cd /etc/shadowsocks-libev/
wget https://github.com/shadowsocks/v2ray-plugin/releases/download/v1.3.2/v2ray-plugin-linux-amd64-v1.3.2.tar.gz

tar -xvf v2ray-plugin-linux-amd64-v1.3.2.tar.gz
rm v2ray-plugin-linux-amd64-v1.3.2.tar.gz
mv v2ray-plugin_linux_amd64 v2ray-plugin
```

### 9. Редактируем конфиг под наши параметры

```shell
# shell
vi /etc/shadowsocks-libev/config.json
```

```json5
// config.json
{
    "server":["12.34.56.78"],
    "mode":"tcp_and_udp",
    "server_port":9388,
    "local_port":1080,
    "password":"12345678ab",
    "timeout":300,
    "method":"xchacha20-ietf-poly1305",
    "nameserver":"1.1.1.1",
    "no_delay": true,
    "fast_open": true,
    "reuse_port": true,
    "plugin":"/etc/shadowsocks-libev/v2ray-plugin",
    "plugin_opts":"server"
}
```

### 10. Перезапускаем службу

```shell
service shadowsocks-libev restart
service shadowsocks-libev status
```

### 11.Скачиваем [плагин v2ray][win-v2ray] для Windows и донастраиваем клиент

<br><hr>

# Подключаем устройство на базе Android

### 12. Устанавливаем ShadowSocks из GooglePlay (разработчик: Max Lv)

### 13. Устанавливаем [плагин v2ray][android-v2ray] из F-Droid

### 14. Запускаем Windows-клиент

```text
ПКМ => Серверы => Поделиться конфигурацией сервера
```

### 15. На android-устройстве сканируем QR-код и выбираем плагин V2Ray

<hr><br>

[win-client]: https://github.com/shadowsocks/shadowsocks-windows/releases

[server-v2ray]: https://github.com/shadowsocks/v2ray-plugin/releases

[win-v2ray]:https://github.com/shadowsocks/v2ray-plugin/releases

[android-v2ray]:https://f-droid.org/packages/com.github.shadowsocks.plugin.v2ray/
