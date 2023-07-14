![Logo](Git-Logo-1788C.png) 
# Работа с Git
#### на примере работы с Git в VsCode
## 1. Проверка наличия установленного Git
 В терминале выполнить команду `git version` Если Git установлен, появится версия программы, иначе будет сообщение об ошибке.
## 2. Установка Git
Загружаем последнюю версию Git с сайта: [загрузка Git](https://git-scm.com/downloads). 
Устанавливаем с настройками по умолчанию.
## 3. Настройка Git.
При первом использовании Git необходимо представиться. Для этого нужно ввести в терминале две команды:
 ```
  git config --global user.name "Ваше имя английскими буквами" git config --global user.email ваша почта@example.com 
 ```
 ## 4. Инициализация репозитория.
 В терминале переходим к папке в которой хотим создать репозиторий. Выполняем команду
 ```
 git init
 ```
 ## 5. Запись изменений в репозиторий.
 Основной инструмент, используемый для определения, какие файлы в каком состоянии находятся — это команда 
 ```
 git status
 ```
 Если вы выполните эту команду сразу после клонирования, вы увидите что-то вроде этого:

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```
Это значит, что в каталоге нет неотслеживаемых файлов.
Предположим,вы добавили простой файл README. Если этого файла раньше не было, и вы выполните git status, вы увидите свой неотслеживаемый файл вот так:
```

$ echo 'My Project' > README
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README

nothing added to commit but untracked files present (use "git add" to track)
```
Понять, что новый файл README неотслеживаемый можно по тому, что он находится в секции «Untracked files» в выводе команды `git status`. Статус Untracked означает, что Git видит файл, которого не было в предыдущем коммите.
Для того чтобы начать отслеживать (добавить под версионный контроль) новый файл, используется команда:
 ```
 git add

 ``` 
 Чтобы начать отслеживание файла README, вы можете выполнить следующее:
```

$ git add README
```
Если вы снова выполните команду `git status`, то увидите, что файл README теперь отслеживаемый и добавлен в индекс:
```

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)

    new file:   README
```

Вы можете видеть, что файл проиндексирован, так как он находится в секции "Changes to be committed". Если вы выполните коммит в этот момент, то версия файла, существовавшая на момент выполнения вами команды `git add`, будет добавлена в историю коммитов.
Чтобы узнать, что конкретно поменялось, а не только какие файлы были изменены — вы можете использовать команду:
 ```
 git diff

 ```
Она показывает вам непосредственно добавленные и удалённые строки — разницу между сохранёнными версиями.
Простейший способ зафиксировать изменения — это набрать:
 ```
 git commit

 ```
Эта команда откроет выбранный вами текстовый редактор.
Чтобы "включить" запись нужно нажать `i` записать комментарий, нажать `Esc`-`:`-`w`-`q` так мы выйдем из редактора.
Есть способ быстрее,можно набрать комментарий к коммиту прямо в командной строке,выполнив команду:
 ```
 git commit -m "coment"

 ```
  или
   ```
   git commit -am "coment"

   ```
   Чтобы еще и проиндексировать.

## 6. Просмотр истории коммитов.
Чтобы просмотреть историю коммитов используй команду:
```
git log

```
 Посмотреть в кратком варианте:
```
git log --oneline

```
## 7. Перемещения между сохранениями.
Чтобы переместиться между сохранёнными версиями нужно набрать команду:
```
git checkout <хеш коммита>

```

 Между ветками:
 ```
 git checkout <имя ветки>

 ```
  и т.д.

ВАЖНО! Всегда возвращаться на главную ветку: `master`

## 8. Игнорирование файлов.
Для того, чтобы исключить из отслеживания в репозитории определенные файлы или папки, необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны , соответствующие таким файлам или папкам.
## 9. Создание веток в Git.
По умолчанию имя основной ветки в Git- `master.`
Создать ветку можно командой:
 ```
git branch <название новой ветки>

```
Список веток в репозитории можно посмотреть с помощью команды 
```
git branch 

```
Текущая ветка будет отмечена звездочкой: **\*master**
Так же можно использовать команды: 
```
git checkout -b <название ветки>

```
или 
```
git switch -c <название ветки>

```
С их помощью можно одновременно создать ветку и переключиться на неё.

## 10. Слияние веток и разрешение конфликтов.
Для слияние выбранной ветки с текущей нужно выполнить команду: 
```
git merge <название выбранной ветки>

```
Если была изменена одна и та же часть файла в обеих ветках,то может возникнуть конфликт, который потребует участия пользователя. VsCode предлагает варианты разрешения и чтобы разрешить конфликт, нужно выбрать один из вариантов, либо объединить содержимое по-своему.
ВАЖНО!
После разрешения конфликта нужно выполнить коммит слияния.
## 11. Удаление веток.
Чтобы удалить ветку нужно выполнить команду:
```
git branch -d <название ветки>

```
ВАЖНО! 
Удалить ветку в которой сейчас находишься невозможно. Команды удаления стоит выполнять только из основной ветки,к примеру из ветки `master`.
Неслитые ветки так же Git не удаляет стандартной командой. Их можно удалить принудительно с помощью команды:
```
git branch -D <имя ветки>

```
## 12. **Работа с удаленными репозиториями**
1. Создать аккаунт на GitHub.
2. Создать локальный репозиторий.
3. Создать удаленный репозиторий.
4. Связать удаленный репозиторий с локальным.
   Добавить удаленный репозиторий к проекту
   ```
   gir remote add <origin> <url - адрес репозитория в сети>
   
   ```
```C#
while(count > 0)
{
count --;
}

```


Для получения и слияния изменений из удаленного репозитория используется команда

`git pull`
## 13.  Pull request.
Для того, чтобы отправить запрос на изменения чужого репозитория нужно:

* В своем аккаунте на GitHub создать копию нужного репозитория с помощью кнопки `fork`.
* Клонировать копию репозитория на локальный компьютер.
* Создать новую ветку.
* Произвести изменения или добавить файлы.
* Зафиксировать изменения(коммиты).
* Отправить изменения на GitHub. 
* На сайте GitHub выполнить `pull request`(предложить изменения).