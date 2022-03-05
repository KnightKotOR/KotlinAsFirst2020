- Копирую форк
`git clone https://github.com/KnightKotOR/KotlinAsFirst2020.git`
- Открываю локальную копию
`cd  KotlinAsFirst2020`
- Указываю в качестве апстрима свой форк KotlinAsFirst2021
`git remote add -f upstream-my https://github.com/KnightKotOR/KotlinAsFirst2021.git`
- Создаю ветку backport и перехожу на нее
`git checkout -b backport `
- Переношу решения из upstream-my в backport
git cherry-pick d535f3592006b8f2593c9f881d72c05164aadc13...FETCH_HEAD`
- Указываю в качестве второго апстрима форк KotlinAsFirst2021 пары
`git remote add -f upstream-theirs https://github.com/yrmint/KotlinAsFirst2021.git`
- Перехожу на мастер
`git checkout master`
- Заполняю ветку своим решением
`git merge backport`
- Заполняю ветку решением коллеги с приоритетом на его решение
`git merge upstream-theirs/master -Xtheirs`
- Cоздаю и делаю коммит remotes
`git remote -v > remotes`
`git add remotes`
`git commit -m "Remotes"`
- Создаю и делаю коммит howto
`touch howto.md`
`git add howto.md`
`git commit -m "Howto"`
- Пушу мастер и бэкпорт
`git push `
`git push --set-upstream origin backport`
