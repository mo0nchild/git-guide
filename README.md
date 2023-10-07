# Git
**Система контроля версии, или VCS** (**V**ersion **C**ontrol **S**ystem) - это программное обеспечение, которое помогает отслеживать изменения в программных, текстовых файлах, больших документах, веб-сайтах и так далее.<br/>
**Git** - один из примеров системы контроля версий, он позволяет хранить, изменять и анализировать историю проектов.
**Git** - незаменимый в команде инструмент, ведь он помогает объединять результаты нескольких человек. 
**Командная строка** (**C**ommand **L**ine **I**nterface, **CLI**) - тоже интерфейс, только текстовый.

---

## Команды для работы с консолью

 **pwd** ( **p**rint **w**orking **d**irectory) - путь к текущей директории. 
```
$ pwd
```
**cd** (**c**hange **d**irectory) - сменить директорию. 
```
$ cd c:/
```
```
$ cd .. #переход на уровень выше
```
**ls** (**l**ist **d**irectory **c**ontents) - вывести содержимое директории
```
$ ls
```
**touch** - создать файл. 
```
$ touch newFile.txt
```
**mkdir** - создать файл. 
```
$ mkdir newDir
```
**mkdir -p ../../..** - создание целой структоры директорий
```
$ mkdir -p dir/dir-inside/dir-deeper-inside 
```
**cp** - копирование файлов
```
$ cp index.html src/
```
**mv** - перемещение файлов и директорий. 
```
$ mv newFile.txt ./newDir
```
**cat** (**c**oncatenate **a**nd **p**rint) - распечатывает, то что содержится в файле. 
```
cat newFile.txt
```
**rm** - удаление файла. 
```
$ rm newFile.txt 
```
**rmdir** - удаление директории. 
```
$ rmdir newDir 
```bush
Чтобы выполнить несколько команд в одной строке, нужно записывать их через **&&**. 
```
$ cd .. && touch newFile.txt && ls
```

---

##Git команды
**git version** - получение текущей версии git. 
```
$ git version
```
**git config --global user.name "..."** 
**git config --global user.email "..."** - настройка конфигурации. 
```
$ git config --global user.name "uran1a"
$ git config --global user.email "9797171z@mail.ru"
```
**cat ~/.gitconfig** - распечатывает текущую конфигурацию. 
```
$ cat ~/.gitconfig
```
**git config --list** - просмотр текущую конфигурацию. 
```
$ git config --list
```
**git init** - инициализация локального репозитория. 
```
$ git init 
```
**git status** - показывает состояние рабочего дерева. 
```
$ git status
```
**rm -rf .git** - удаление папки как репозитория. 
```
rm -rf .git 
```
**git add "..."** - подготовка файлов к сохранению
```
$ git add "newFile.txt"
```
**git add --all** - подготовка к сохранению сразу всех файлов. 
```
$ git add --all 
```
**git add .** - сохранить текущую папку. 
```
$ git add . 
```
**git commit -m "..."** - создание коммита. 
```
$ git commit -m "init: start project"
```
**git log** - просмотр истории коммитов. 
```
$ git log
```
**git log --oneline** - получение сокращенного лога. В терминале появятся *сокращенный хеш* и комментарий каждого коммита. *Сокращенный хеш* (то есть несколько символов полного) можно использовать точно так же, как и полный.
```
$ git log --oneline
cfe1e31 (HEAD -> master, origin/master) init: start project
```
Файл **HEAD** - один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).
Если нужно передать последний коммит, то вместо его хеша можно просто написать слово *HEAD* - Git поймет, что вы имели в виду последний коммит.

---

##GitHub
**GitHub** - платформа для хранения IT-проектов и совместной работы над ними с использованием Git.
**SSH** - протокол, который обеспечивает безопасностный обмен данными в сети и использует для этого ключи.
**SSH-ключ** - ваш виртуальный модификатор в GitHub. SSH-ключ состоит из двух частей - публичный и приватный. публичный ключ зашифровывает данные, а приватный - расшифровывает. 

---

**git remote add "название удаленного репозитория" "SSH или URL"** - привязка удаленного репозитория к локальному 
```
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git
```
**origin** (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один).

**git remote -v** - получение большей информации о выводе. Помогает убедиться, что репозитории связаны.
```
$ git remote -v
```
**git push -u "название удаленного репозитория" "название ветки"** - связывание локальной ветки с одноименной удаленной веткой. 
```
$ git push -u origin master
```


---

##Хеш - идентификатор коммита
**Хеширование** - это способ преобразовать набор данных и получить их "отпечаток" (fingerprint).
Git хеширует (преобразует) информацию о коммите с помощью алгоритма **SHA-1** (Secure Hash Algorithm - "безопастный алгоритм хеширования") и получает для каждого коммита свой уникальный *хеш - результат хеширования*. 
Если посчитать хеш одного и того же файла (одним и тем же алгоритмом) на двух разных компьютерах, то результат будет *гарантированно одинаковым*.
Все хеши и таблицы *хеш -> информация о коммите* Git сохраняет в служебные файлы. Они находятся в скрытой папке *.git* в репозитории проекта. 

## Статусы файлов в Git
- **untracked** (неотслеживаемый) - git "видит", что такой файл существует, но не следит за изменениями в нем.
- **staged** (подготовленный) - после выполнения команды *git add* файл попадает в *staging area*, то есть в список файлов, который войдет в коммит. В этот момент файл находятся в состоянии *staged*. 
- **tracked** (отслеживаемый) - в него попадают файлы, которые были зафиксированы с помощью *git commit*, а также файлы, которые были добавлены в *staging area* командой *git add*. То есть все файлы, в которых Git так или иначе отслеживает изменения.
- **modified** (измененный) - Git сравнил содержимое файла с последней сохранненой версией и нашел отличия. Например, файл был закоммичен и после был изменен.

##Conventional Commits

Conventional Commits - это простое соглашение о том, как нужно писать сообщения commit`ов. 
Сообщения commit`ов должны быть следующей структуры:
```
<type>[optional scope]: <descroption>
```

Commit’ы могут содержать следующие структурные элементы:
- fix: при исправляет ошибку в вашем коде. 
    ```
    init: start project
    init: start task
    ```
- feat: при добавляет новую функцию в ваш коде. 
    ```
    feat: add basic page layout
    feat: implement search box
    ```
- init: при начале проекта или задания. 
    ```
    fix: implement correct loading data from db
    fix: correct minor typos in code
    ```
- refactor: при улучшение кода, без изменения функциональности. 
    ```
    refactor: change structire of the project
    refactor: rename vars for better readabiliry
    ```
- docs: используется при работе с документацией/readme проекта 
    ```
    docs: update readme with additional information
    docs: update description of run() method
    ```

##Как исправить коммит

**--amend** рассчитан на работу c последним коммитом (HEAD). 
Дополнить коммит новыми файлами можно c помощью:

```
$ git add file.txt
$ git commit --amend --no-edit
```

Благодаря опции **--no-edit** сообщение к коммиту останется таким, каким и было.
Изменить сообщение к коммиту позволяет команда:
```
$ git commit --amend -m "Обновлённое сообщение коммита"
```

##Откат коммита, изменений, списка коммита

**git restore --staged \<file>** - убрать файл из *staging area* (убрать файл из списка "на коммит").
```
$ git restore --staged "file.txt"
```

**git reset --hard \<commit hash>** - вернуть состияние репозитория к более раннему коммиту. Более поздние коммиты потеряются!
```
$ git log --oneline
b576d89 ...
$ git reset --hard b576d89
```

**git restore \<file>** - изменения в файле «откатятся» до последней версии, которая была сохранена через *git commit* или *git add*. 
```
git restore file.txt