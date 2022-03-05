git clone https://github.com/KnightKotOR/KotlinAsFirst2020.git //Копирую форк
cd  KotlinAsFirst2020 //Открываю локальную копию
git remote add -f upstream-my https://github.com/KnightKotOR/KotlinAsFirst2021.git //Указываю в качестве апстрима свой форк KotlinAsFirst2021
git checkout -b backport //Создаю ветку backport и перехожу на нее
git cherry-pick d535f3592006b8f2593c9f881d72c05164aadc13...FETCH_HEAD //Переношу решения из upstream-my в backport
git remote add -f upstream-theirs https://github.com/yrmint/KotlinAsFirst2021.git //Указываю в качестве второго апстрима форк KotlinAsFirst2021 пары
git checkout master //Перехожу на мастер
git merge backport //Заполняю ветку своим решением
git merge upstream-theirs/master -Xtheirs //Заполняю ветку решением коллеги с приоритетом на его решение
git remote -v > remotes //Создаю и делаю коммит remotes
git add remotes
git commit -m "Remotes"
touch howto.md //Создаю и делаю коммит howto
git add howto.md
git commit -m "Howto"
git push //Пушу мастер и бэкпорт
git push --set-upstream origin backport
