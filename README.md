## siteTransfer
Дополнение **siteTransfer** создаёт архив для упрощённого переноса сайта на другой сервер. В следующие файлы вносятся изменения, которые позволяют не прописывать в них новые пути при переносе:

*   core.config.php,
*   /manager/core.config.php,
*   /connectors/core.config.php

Файл **/core/config/config.inc.php** переименовывается в **/core/config/config.inc.php.backup**. В нём так же нет необходимости прописывать пути - только доступ к новой базе данных. Вместе с архивом файлов скачивается дамп базы данных. Папка кеша не включается в архив, так что чистить кеш перед началом переноса необязательно.

> Для создания архива используются команды **mysqldump** и **tar**.

Компонент можно использовать просто для быстрого создания бэкапа сайта.

### Алгоритм переноса сайта с помощью siteTransfer

1.  Создаём и скачиваем архив сайта в разделе компонента в админке. Не забудьте нажать кнопку "Удалить архив", когда файл будет загружен.
2.  На новом сервере создаём пустую базу данных. Импортируем в неё дамп из загруженного архива.
3.  Загружаем архив на новый сервер и распаковываем его.
4.  В файле **/core/config/config.inc.php.backup** прописываем название базы, имя пользователя и пароль. Файл переименовываем в **/core/config/config.inc.php**.

После этого сайт должен сразу заработать.
