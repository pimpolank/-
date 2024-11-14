## Задача 1
На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.

![image](https://github.com/user-attachments/assets/b63f179c-3b5c-4bf2-890f-f3173bf908a1)

```
git commit
git tag in
git branch first
git branch second
git commit
git commit
git checkout first
git commit
git commit
git checkout master
git merge first
git checkout second
git commit
git commit
git rebase master
git checkout master
git merge second
git checkout in
```

## Задача 2
![image](https://github.com/user-attachments/assets/b039bc9a-716a-442d-b62b-24e9d8602687)


```
naiba@r1ken MINGW64 ~/Desktop
$ mkdir repo

naiba@r1ken MINGW64 ~/Desktop
$ cd repo

naiba@r1ken MINGW64 ~/Desktop/repo
$ git init
Initialized empty Git repository in C:/Users/naiba/Desktop/repo/.git/

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ git config --global user.name "coder1"

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ git config --global user.email "coder1@example.com"

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ echo "print('Hello, World!')" > prog.py
bash: !': event not found

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ echo "print('Hello, World')" > prog.py

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ git add prog.py

naiba@r1ken MINGW64 ~/Desktop/repo (master)
$ git commit -m "Added prog.py"
[master (root-commit) 6bcd0cb] Added prog.py
 1 file changed, 1 insertion(+)
 create mode 100644 prog.py

```

## Задача 3
![image](https://github.com/user-attachments/assets/d3c67b90-31cf-4d03-a2b8-2caffd87eeb9)


```
# Создание bare-репозитория и загрузка содержимого локального репозитория
git init --bare server 
cd C:/Users/naiba/Desktop/repo
git remote add server C:/Users/naiba/Desktop/server
echo "print('Hello, World!')" > prog.py
git add prog.py
git commit -m "Added prog.py"
git push server master
git remote -v

# Клонирование репозитория server и работа с coder2
mkdir coder2_repo
cd coder2_repo
git clone C:/Users/naiba/Desktop/server
cd server
git config user.name "coder2"
git config user.email "coder2@example.com"
echo "# Программа" > readme.md
echo "Это описание программы." >> readme.md
git add readme.md
git commit -m "docs"
git push origin master

# Coder1 получает актуальные данные с сервера 
cd C:/Users/naiba/Desktop/repo
git pull server master
echo "## Авторы" >> readme.md
echo "- coder1 <coder1@example.com>" >> readme.md
git add readme.md
git commit -m "coder1 info"
git push server master

# Coder2 добавляет информацию о себе и решает конфликты
cd C:/Users/naiba/Desktop/coder2-repo/server
git pull origin master
echo "- coder2 <coder2@example.com>" >> readme.md
git add readme.md
git commit -m "coder2 info"
git push origin master

# Проверка лога коммитов
git log -n 5 --graph --decorate --all
```

## Задача 4

![image](https://github.com/user-attachments/assets/ed1f6016-81c5-4d76-94ba-9b1dad04c13e)


```
import os
import subprocess

def get_git_objects():
    try:
        result = subprocess.run(
            ['git', 'rev-list', '--all'],
            stdout=subprocess.PIPE,
            stderr=subprocess.PIPE,
            text=True,
            check=True
        )
        objects = result.stdout.splitlines()

        for obj in objects:
            print(f"Git Commit: {obj}")
            try:
                content = subprocess.run(
                    ['git', 'cat-file', '-p', obj],
                    stdout=subprocess.PIPE,
                    stderr=subprocess.PIPE,
                    text=True,
                    check=True
                )
                print(content.stdout)
            except subprocess.CalledProcessError as e:
                print(f"Error {obj}: {e.stderr}")

    except subprocess.CalledProcessError as e:
        print(f"Error: {e.stderr}")

if __name__ == "__main__":
    if not os.path.exists('.git'):
        print("Git not found")
    else:
        get_git_objects()
```
