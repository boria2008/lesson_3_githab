* ## Команда задания или изменения имя пользователя и адреса электронной почты для привязки к ним фиксаций изменений в папке.
```
git config --global user.name "user_name"

git config --local user.name "user_name"

git config --global user.email "user_email"

git config --local user.email "user_email"
```
* ## Кэширование учётных данных
```
git config --global credential.helper cache
```
*Кэшировать учётные данные можно с помощью параметра config с флагом --global. Так вы избавитесь от необходимости вручную вводить имя пользователя и пароль при создании нового коммита.*

* ## Инициализация репозитория.
```
git init
```
* ## Добавление отдельных файлов или всех файлов в область подготовленных файлов
~~~
git add somefile.js
~~~
*можно добавить все файлы и папки в эту область, предоставив wildcard . вместо имени файла:*
~~~
git add .
~~~
* ## Проверка статуса репозитория
```
git status
```
* ## Внесение изменений однострочным сообщением или через редактор
```
git commit -m "Your short summary about the commit" 
```
* ## Просмотр истории коммитов с изменениями
*Просматривать изменения, внесённые в репозиторий, можно с помощью параметра log. Он отображает список последних коммитов в порядке выполнения. Кроме того, добавив флаг -p, вы можете подробно изучить изменения, внесённые в каждый файл.*
```
git log -p
```
* ## Просмотр заданного коммита
```
git show 1af17e73721dbe0c40011b82ed4bb1a7dbe3ce29
```
*Также можно использовать сокращённый хеш.*
```
git show 1af17e
```
* ## Просмотр изменений до коммита
*Можно просматривать список изменений, внесённых в репозиторий, используя параметр diff. По умолчанию отображаются только изменения, не подготовленные для фиксации.*
```
git diff
```
* ## Создание новой ветки и переход в неё
```
git branch new_branch_name
```
*Но Git не переключится на неё автоматически. Для автоматического перехода нужно добавить флаг -b и параметр checkout*
```
git checkout -b new_branch_name
```
* ## Просмотр списка веток
```
git branch
```
*Также можно вывести список удалённых веток с помощью флага -a.*
```
git branch -a
```
* ## Слияние двух веток
 *Объединить две ветки можно параметром merge с указанием имени ветки. Команда объединит указанную ветку с основной.*
 ```
 git merge existing_branch_name
 ```
 *Если надо выполнить коммит слияния, выполните команду git merge с флагом **--no-ff.***
 ```
 git merge --no-ff existing_branch_name
 ```
*Для просмотра подготовленных изменений необходимо добавить флаг **--staged.***
```
git diff --staged
```
*Также можно указать имя файла как параметр и просмотреть изменения, внесённые только в этот файл.*
```
git diff somefile.js
```
* ## Удаление отслеживаемых файлов из текущего рабочего дерева
*Удалять файлы из текущего рабочего дерева можно с помощью параметра rm. При этом файлы удаляются и из индекса.*
```
git rm dirname/somefile.js
```
* ## Переименование файлов
*Переименовать файл или папку можно параметром* **mv**. *Для него указывается источник source и назначение destination. Источник — реально существующий файл или папка, а назначение — существующая папка.*
```
git mv dir1/somefile.js dir2
```
*При выполнении команды файл или папка, указанные как источник, будут перемещены в папку назначения. Индекс будет обновлён соответственно, но изменения нужно записать.*
* ## Изменение последнего коммита
*Внести изменения в последний коммит можно параметром commit с флагом* __--amend__. *Например, вы записали изменения, внесённые в ряд файлов, и поняли, что допустили ошибку в сообщении коммита. В этом случае можете воспользоваться указанной командой, чтобы отредактировать сообщение предыдущего коммита, не изменяя его снимок.*
```
git commit --amend -m "Updated message for the previous commit"
```
*Также можно вносить изменения в файлы, отправленные ранее. Например, вы изменили несколько файлов в ряде папок и хотите их записать как единый снимок, но забыли добавить в коммит одну из папок. Чтобы исправить такую ошибку, достаточно подготовить для фиксации остальные файлы и папки и создать коммит с флагами* **--amend** *и* **--no-edit**.
```
git add dir1
git commit

# Here you forgot to add dir2 to commit, you can execute the
following command to amend the other files and folders.

git add dir2
git commit --amend --no-edit
```
>Внимание! Не изменяйте публичные коммиты.
С помощью amend прекрасно исправляются локальные коммиты, а исправления можно передать в общий репозиторий. Однако изменять коммиты, уже доступные другим пользователям, не следует. Помните, что изменённые коммиты являются совершенно новыми, а предыдущий коммит уже не будет доступен в текущей ветке. Последствия будут такими же, как при отмене изменений публичного снимка.

