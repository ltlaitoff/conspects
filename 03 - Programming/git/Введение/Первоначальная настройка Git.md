---
tags:
  - git
  - git/config
---
### Первоначальная настройка Git

После того как Git был установлен самое время настроить среду для работы с ним под себя. Это нужно сделать только один раз - при обновлении версии Git настройки сохранятся. Но, при необходимости, их можно в любой момент заменить

В состав Git входит утилита `git config`, которая позволяет просматривать и настраивать параметры, контролирующие все аспекты работы Git, а также его внешний вид. Эти параменты могут быть сохраненны в трёх местах:
1. Файл `[path]/etc/gitconfig` содержит значения, общие для всех пользователей системы и для всех их репозиториев. Если при запуске `git config` указать парамент `--system`, то параметры будут читаться и сохранятся именно в этот файл. Так как этот файл является системным, то вам потребуются права суперпользователя для внесения изменений в него
2. Файл `~/.gitconfig` или `~/.config/git/config` хранит настройки конкретного пользователя. Этот файл используется при указании парамента `--global` и применяется ко **всем** репозиториям, с которыми вы работаете в текущей системе.
3. Файл `config` в каталоге Git (`.git/config`) репозитория, который вы используете в данный момент, хранит настройки конкретного репозитория. Вы можете заставить Git читать и писать в этот файл с помощью параметра `--local`, но на самом деле это значение по умолчанию. Неудивительно, что нужно находится где-то в репозитории Git, чтобы эта опция работала правильно

Настройки на каждом следующем уровне подменяют настройки из предыдущих уровней, то есть значения в `.git/config` перекрывают сответствубщие значения в `[path]/etc/gitconfig`.

Чтобы посмотреть все установленные настройки и узнать где именно они заданы, используйте команду:
```
$ git config --list --show-origin
```

## Имя пользователя
Первое что следует сделать после установки git - указать ваше имя и email. Это важно поскольку каждый коммит содержит эту информацию, и она включена в коммиты, передаваемые вами, и не может быть измененна:
```
$ git config --global user.name "NAME"
$ git config --global user.email email@example.com
```

Если нужно для каких-то отдельных проектов указать другое имя - в команду достаточно убрать `--global`

## Выбор редактора
По умолчанию git использует стандартный редактор вашей системы, которым обычно является vim

Чтобы изменить редактор можно ввести команду:
```
$ git config --global core.editor emacs
```
Вместо emacs может быть любой другой текстовый редактор

В `Windows` следует указать полный путь к исполняемому файлу при установке другого редактора по умолчанию. 

Например, установим Notepad++  в качестве редактора по умолчанию:
```
$ git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe'
-multiInst -notabbar -nosession -noPlugin"
```

## Настройка ветки по умолчанию
Когда вы иинициализируете репозиторий командой `git init`, Git создает ветку с именем *master* по умолчанию.

Если вы хотите установить ветке по умолчанию имя, например, *main*, выполните следующую команду:
```
$ git config --global init.defaultBranch main
```


## Проверка настроек
Если вы хотите проверить используемую конфигурацию, можете использовать `git config --list`, чтобы показать все настройки, которые Git найдёт:
```
$ git config --list
core.editor=vim  
core.quotepath=off  
include.path=~/.gitconfig.user  
user.name=Ivan Baluta  
user.email=ltlaitoff@gmail.com  
...
```

Некоторые ключи (названия) настроект могут отображатся несколько раз, потому что Git читает настройки из разных файлов (например, из `/etc/gitconfig` и `~/.gitconfig`). В таком случае Git использует последнее значение для каждого ключа.

Также вы можете проверить значение конкретного ключа, выполнив команду `git config <key>`
```
$ git config user.name
Ivan Baluta
```

**!** Так как Git читает значение настроек из нескольких файлов, возможна ситуацияк когда Git использует не то значение что вы ожидали. В таком случае вы можете спросить git об `origin` этого значения. Git выведет имя файла, из которого значение для настройки было взято последним:
```
$ git config --show-origin rerere.autoUpdate
file:/home/johndoe/.gitconfig   false
```
