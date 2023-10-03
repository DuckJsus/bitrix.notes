## Настройка git на виртуалке/проде

---

#### Важно! Ознакомьтесь перед началом работы

---

Для Bitrix должно быть два репозитория:
* Корневая папка (в gitignore обязательно добавляется папка bitrix)
* Ядро - папка **bitrix** (в gitignore добавляются файлы с доступами к базе (.settings.php и php_intrface/dbconn.php))

Дальнейшие шаги выполняются отдельно для каждого из двух репозиториев

---

### Следующий этап выполняется в любом случае (и для прода и для теста)
1. Инициализация репозиория
```
git init
```

2. Указываем свое имя и мейл
```
git config --global user.name "Ваше Имя"
git config --global user.email "you@example.com"
```

3. Создаем .gitignore файл

Готовые .gitignore файлы лежат в соответствующей папке

4. Добавляем все файлы в гит и коммитим
```
git add .
git commit -m 'Initial commit'
```

5. Переименовываем ветку (**! пункт чисто для теста !**)
```
git branch -m новое-имя-ветки
```

---
---


### Добавление remote связи с Gitlab

---

#### Для теста, с помощью http

```
git remote add origin http://login:password@gitlab.example.com/example-group/example-project.git
```
> Note: Если логин содержит символ @, то его необходимо заменить на 40%

---

#### Для прода, с помощью SSH

Генерим и добавляем ключ в Gitlab

> Рекомендуется использование SSH ключей типа ed25519, именно они далее будут использоваться в инструкции

* В ssh консоли в корневой папке запускаем скрипт:
```
ssh-keygen -t ed25519 -C "Comment"
```
> В качестве Comment подставляем мейл учетки gitlab, для которой делаем доступ

* Жмем Enter. Отобразится вывод, аналогичный следующему:
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25519):
```
* Жмем Enter, после чего появится:
```
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```
* И снова Enter

Генерируются открытый и закрытый ключи. Добавьте открытый ключ SSH в свою учетную запись GitLab. Ключ хранится в файле c окончанием .pub
> Добавляются в Gitlab в _Edit profile -> SSH Keys_

Добавляем remote:

```
git remote add origin git@sitename:example-group/example-project.git
```

---
---


### Действия после добавления remote

---

#### Для прода

```
git push origin master
```

---

#### Для теста

```
git fetch origin
git checkout master
```

---