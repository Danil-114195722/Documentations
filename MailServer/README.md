# Как настроить почтовый сервер (только на отправку писем)
### (Вариант для настройки полноценного почтового сервера - iRedMail)

<br>

```shell
apt install mailutils
```

```shell
dpkg-reconfigure postfix
```
1. Internet site
2. Домен, привязанный к серверу
3. Юзер, на которого будут приходить письма для root и postmaster пользователей (vmail)
4. Список доменов, которые будут учитываться сервером как конечное назначение на себя
   (your-domain.ru, localhost.ru, localhost)
5. Оставляем NO
6. Оставляем без изменений
7. Лимит на тело сообщения (0 для отключения лимита)
8. Оставляем без изменений
9. Можно выбрать ipv4


```shell
nano /etc/postfix/main.cf
```
```shell
# in file /etc/postfix/main.cf

inet_interfaces = loopback-only
```

```shell
systemctl restart postfix
```

Тестовая отправка письма (лучше отправлять на Яндекс, потому что он просто добавляет письмо в спам, а Гугл отфильтровывает его и не показывает вообще)
```shell
echo "Test body of the email" | mail -s "Test email from server" your_email@yandex.ru

su user -c "echo 'Test body of the email' | mail -s 'Test email from server' your_email@yandex.ru"
```
