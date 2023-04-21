# Git :octocat:
[⚙️ Menu](README.md)

### Работа в команде 1.
```c
Тим лид fork проекта (если он есть)
Тим лид клонирует себе репозиторий и выполняет первичную настройку
Тим лид раздаёт роли и ставит адекватные задачи
Тим лид делает
git add -A // добавляем изменения
git commit -m "initial commit" // добавляем комментарий
git push origin main (или master) // стягиваем все последние изменения на ветке

Работа каждого члена команды:
git clone 
git checkout -b BRANCHNAME // создание своей ветки из ветки в которой находишься (без флага -b будет просто переход на данную ветку)
пишете код ...
git add -A // добавляем изменения
git commit -m "MESSAGE" // добавляем комментарий
git checkout main (или master) // переходим на main
git pull origin main (или master) // стягиваем все последние изменения на ветке
Разрешаете конфликты
git checkout BRANCHNAME // переходим на нашу ветку
git merge main (master) // мерджим с мейном
git push origin BRANCHNAME // пушим на указанную ветку
Открываете pull request на GitHub
Просите тим лида принять pull request и выполнить слияние в main
Чтобы продолжить кодировать:
git checkout main
git pull origin main
продолжи с пункта 2
```

### Способ 2. от Артема
```c
Это флоу через ребэйз

git checkout develop
git fetch origin develop
git checkout -b myBranch
кодим 
git add .
git commit -m "Made some changes on myBranch"
тянем изменения с дева
git fetch origin develop
git rebase origin/develop
если возникли конфликты - решаем их и потом
git add .
git rebase --continue
git push origin myBranch

А это через мердж 

git checkout develop
git fetch origin develop
git checkout -b myBranch
кодим
git add .
git commit -m "Made some changes on myBranch"
тянем апдейты с дева
git fetch origin develop
мерджим пришедшие изменения в нашу ветку
git merge origin/develop
если есть конфликты htiftv потом
git add .
git commit -m "Resolved conflicts"

git push origin myBranch

у вас ветки создаются в жире, поэтому новую ветку создавать не надо
```

### Доп

```c
git merge --abort // отменить мердж когда находитесь в процессе слияния или решаете конфликты
$ git reset --soft HEAD~1 // если вы хотите откатиться на комит
после можно проверить написав
$ git log
```
