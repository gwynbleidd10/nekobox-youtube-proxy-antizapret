# Настройка клиента Nekobox для обхода замедления Youtube с использованием прокси сервера XRay

## Загрузка клиента, актуальных баз и конфига
1. Загрузить клиент [Nekobox](https://github.com/MatsuriDayo/nekoray). Последняя версия на момент написания гайда [4.0-beta3](https://github.com/MatsuriDayo/nekoray/releases/tag/4.0-beta3)
2. Загрузить актуальная базы и закинуть их в корень клиента с заменой:
- [`antizapret.srs`](https://github.com/savely-krasovsky/antizapret-sing-box/releases/latest/download/antizapret.srs)
- [`geoip.db`](https://github.com/savely-krasovsky/antizapret-sing-box/releases/latest/download/geoip.db)
- [`geosite.db`](https://github.com/savely-krasovsky/antizapret-sing-box/releases/latest/download/geosite.db)
3. Загрузить актуальный конфиг маршрутов из [репозитория](https://github.com/gwynbleidd10/nekobox-youtube-proxy-antizapret/blob/main/Default) и закинуть в папку `/config/routes_box` с заменой
4. На всякий случай сделан бекап первых 2 пунктов в папке `backup`

## Добавление серверов/подписок
Для добавления сервера или подписок (группы серверов, которые могут обновляться автоматически с сервера) необходимо:
1. Поднять свой прокси сервер и произвести настройки или арендовать/попросить и т.д
2. Получить строку подключения/QR код
3. Добавить через пункт `Программа - Добавить профиль из буфера обмена`. После этого у вас появится один или несколько серверов в списке в зависимости от типа строки. Вы можете выбрать любое доступное подключение. Приоритет по надежности:
    - VLESS
    - Shadowsocks
    - ...

## Настройка
С данным конфигом маршрутизация осуществляется по схеме `bypass` т.е. весь трафик проходит напрямую, а те домены/IP что указаны в разделах с типом `proxy` уже идет через внешний прокси сервер. При необходимости можно изменить схему на `proxy` в выпадающем списке `Outbound по умолчанию`, тогда весь трафик будет идти на прокси, а то что в списках `direct` будет идти от провайдера.

Страница маршрутов находится в пункте `Настройки - Настройки маршрутов - Базовые маршруты`. Окно представляет из себя таблицу с 2 строками и 3 столбцами:
- в 1 строке забиваются IP адреса, во 2 строке домены
- в 1 столбце трафик будет идти напрямую от провайдера, во 2 столбце через прокси сервер, в 3 столбце будут блокироваться
![s2](https://github.com/user-attachments/assets/ff6870c4-b2f2-4aaf-a6df-65a11606f913)


Также дополнительно можно прописать кастомные маршруты через `Кастомные маршруты`. [Подробная](https://sing-box.sagernet.org/configuration/dns/rule/#protocol) информация по настройке. Сохранить и перезапустить соединение.
![s3](https://github.com/user-attachments/assets/85226263-423b-4b50-ba76-80640e424a3b)

## Запуск
Для запуска выбираем необходимое подключение - ПКМ - запустить. У меня не работает без включения чекбокса `Режим системного прокси`. Если у вас также то не забывайте включать вместе с включение подключения к прокси.
![s4](https://github.com/user-attachments/assets/3626e285-7767-43fd-ae4d-70a64fbe8e01)
