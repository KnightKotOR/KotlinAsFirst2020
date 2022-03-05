1)Копирую форк
git clone https://github.com/KnightKotOR/KotlinAsFirst2020.git 
2)Открываю локальную копию
cd  KotlinAsFirst2020
3)Указываю в качестве апстрима свой форк KotlinAsFirst2021
git remote add -f upstream-my https://github.com/KnightKotOR/KotlinAsFirst2021.git
4)Создаю ветку backport и перехожу на нее
git checkout -b backport 
5)Переношу решения из upstream-my в backport
git cherry-pick d535f3592006b8f2593c9f881d72c05164aadc13...FETCH_HEAD
6)Указываю в качестве второго апстрима форк KotlinAsFirst2021 пары
git remote add -f upstream-theirs https://github.com/yrmint/KotlinAsFirst2021.git
7)Перехожу на мастер
git checkout master
8)Заполняю ветку своим решением
git merge backport
9)Заполняю ветку решением коллеги с приоритетом на его решение
git merge upstream-theirs/master -Xtheirs
10) оздаю и делаю коммит remotes
git remote -v > remotes
git add remotes
git commit -m "Remotes"
11)Создаю и делаю коммит howto
touch howto.md
git add howto.md
git commit -m "Howto"
12) ушу мастер и бэкпорт
git push 
git push --set-upstream origin backport
