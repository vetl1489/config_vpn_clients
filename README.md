# Настройка клиентов VPN


## Настройка IKEv2/IPsec

Подключение к IKEv2 состоит из двух шагов:
- импортирование сертификата;
- настройка VPN соединения с учетными данными.

Для каждого устройства свое IKEv2 подключение. Одновременное использование одного подключения на разных устройствах приведет к ошибкам.

### Windows (10 и 11)

#### Импорт Сертификата
1. Двойным кликом щелкнуть по сертификату `.cer`.
2. В открывшемся мастере выбрать **Установить сертификат**.
3. Выбрать для кого установить: для текущего пользователя (работает для текущей учетной записи), или для всех пользователей компьютера — будет работать у всех.
4. Поместить сертификат в хранилище, Обзор.
5. В окошке выбрать **Доверенные корневые центры сертификации**. Далее, Готово.
6. На вопрос системы безопасности хотим ли установить сертификат, говорим Да.
#### Настройка VPN:
1. Перейдите в Параметры Windows / Сеть и интернет / VPN / Добавить VPN подключение.
2. Введите данные сервера VPN: 
    - **Поставщик услуг VPN:** Windows (встроенные);
    - **Имя подключения:** на свой вкус;
    - **Имя или адрес сервера:** тот IP, который пришлю;
    - **Тип VPN:** IKEv2;
    - **Тип данных для входа:** Имя пользователя и пароль;
    - **Имя пользователя** и **Пароль**: предоставленные учетные данные.
3. Подключиться к VPN можно теперь щелкнув по иконке сети и выбрав созданное VPN подключение.

### Android
Установить **StrongSwan VPN Client**:
- [Google Play](https://play.google.com/store/apps/details?id=org.strongswan.android&hl=ru&gl=US)
- [F-Droid](https://f-droid.org/en/packages/org.strongswan.android/)

1. Закинуть на телефон файл сертификата `.pem`.
2. Открыть StrongSwan VPN Client, в правом верхнем меню выбрать **Сертификаты СА**.
3. Снова в правом верхнем меню выбрать уже **Import certificate**.
4. В открывшемся файловом менеджере выбираем тот самый файл сертификата `.pem`. Он появится в списке **Imported**.
5. Вернуться на главный экран программы и щелкнуть **Добавить VPN профиль**.
    1. Сервер: тот IP, который пришлю;
    2. VPN тип: IKEv2 EAP (Логин/Пароль)
    3. Логин и пароль: предоставленные учетные данные.
    4. Сертификат СА, снять галочку автоматически, и выбрать сертификат CA. Выбираем свой установленный сертификат в списке **Imported**.
    5. Название профиля на свой вкус.

