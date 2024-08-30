Разбиение монолита на microfrontend'ы.
Стратегия - Изоляция/Вертикальная нарезка
Обоснование:
1. Предполагаю частые обновления и развёртывания (развитие приложения).
2. У разных частей приложения будут разные нагрузки и требования к производительности.
3. Нет сложных бизнес-процессов.
4. Возможен различный технологический стек (при наборе команд).


Список microfrontend'ов: 
1. Microfrontend "Вход/Регистрация пользователя"
   Функции: аутентификация
   Login.js  // Компонент входа пользователя
     Login
     Password
   Registration.js // Компонент регистрации пользователя
     Name
     Description
     AvatarPhotoRef
     Email
     Password   
   
2. Microfrontend "Профиль пользователя" 
   Функции: Редактирование профиля
     Profile.js // Компонент профиля пользователя
       Name
       Description
       AvatarPhotoRef
       Email
       Password

3. Microfrontend "Лента пользователя"
   Функции: показ ленты фотографий пользователя
            переход в профиль пользователя
            сбор/удаление лайков
            удаление фотографий
            загрузка фотографий
              LoadPhoto.js // Компонент загрузки фотографий
                PhotoTitel
                PhotoRef
      UserNewsFeed.js // Компонент ленты пользователя
     

Метод интеграции: Run time
Обоснование:
1. Необходимо развёртывать модули независимо.
2. Необходимо динамически обновлять отдельные модули. 
3. Необходимо сделать масштабирование гибким.

Композиция:
Гибридная, планируется использовать BFF + JavaScript-фреймворки
Обоснование:
1. Важен SEO и быстрый первоначальный отклик.
2. В дальнейшем можно создать богатый интерактивный пользовательский опыт.
3. Приложение должно поддерживать независимое развёртывание отдельных модулей

Фреймворк:
Webpack Module Federation 
У меня не одностраничные приложения 

Коммуникация между микрофронтендами:
Библиотека глобального состояния  Redux
Обоснование:
Нужно тесное взаимодействие и согласованное состояние микрофронтендов.

BFF
1. BFF "Загрузка фотографий"
2. BFF "Вход/Регистрация пользователя"
3. BFF "Профиль пользователя" 
4. BFF "Лента пользователя"
5. BFF "Список пользователей" 
