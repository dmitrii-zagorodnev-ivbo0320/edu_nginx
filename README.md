Этот репозиторий содержит код и документацию для создания собственного Docker-контейнера Nginx и загрузки его в Docker Hub.

Репозиторий включает следующие файлы:
* Dockerfile: Этот файл определяет шаги, необходимые для создания образа Nginx.
* README.md: В этом файле содержатся инструкции по сборке и использованию образа.

Чтобы собрать образ, выполните следующую команду:
```
docker build -t <ваше имя пользователя>/nginx .
```

Чтобы загрузить образ в Docker Hub, выполните следующую команду:
```
docker push <ваше имя пользователя>/nginx
```

После того как образ загружен, вы можете запустить его с помощью следующей команды:
```
docker run -d -p 80:80 <ваше имя пользователя>/nginx
```

Это запустит контейнер, запускающий Nginx на порту 80. После этого вы сможете получить доступ к Nginx, перейдя по адресу http://localhost в вашем браузере.

Я надеюсь, что этот репозиторий будет полезен. Если у вас возникли вопросы, пожалуйста, оставьте комментарий ниже.
