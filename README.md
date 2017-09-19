## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com #Открыть веб страницу по данному адресу
```

## Tasks

- [+] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [+] 2. Ознакомиться со ссылками учебного материала
- [+] 3. Выполнить инструкцию учебного материала
- [+] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
#Устанавливаем нужные параметры для дальнейшей работы
$ export GITHUB_USERNAME=lightman1998 #Задаем значение переменной GITHUB_USERNAME
$ export GITHUB_EMAIL=kall-lightman@yandex.ru #Задаем значение переменной GITHUB_EMAIL
$ alias edit=vi #Выбираем редактор
```

```ShellSession
#Работа с репозиторием, при помощи pull/push, add, status и других комманд
$ mkdir lab03 && cd lab03 #Создаем репо lab03 и переходим в него при помощи команды cd
$ git init #Создание репозитория в существующем каталоге
$ git config --global user.name ${GITHUB_USERNAME} #При помощи config устанавливаем дальнейшие параметры. Для это используем флаг (--global) и прописываем для user.name нашу текущую переменную GITHUB_USERNAME. Так как мы используем флаг (--global), то мы можем делать эту настройку единожды; для остальных случаев данные настройки будут сохранены
$ git config --global user.email ${GITHUB_EMAIL} #Аналогично предыдущему шагу, мы прописываем для user.email нашу текущую переменную GITHUB_EMAIL, которой мы также заранее задали значение
$ git config -e --global #Просмотр результата введенных ранее команд. На экране появились в текстовом редакторе раннее введенные данные
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03 #Добавление нового удаленного Git repo под именем-сокращением 'origin' по данному URL
$ git pull origin master #Извлекли данные с удаленного сервера и слили их с текущей работой
$ touch README.md #Установка времени последнего изменения файла на текущее
$ git status #Проверка текущего состояния
$ git add README.md #Начало остлеживания версионного изменения для README.md
$ git commit -m"added README.md" #Закоммитили изменеие
$ git push origin master #Отправили ветку master на сервер origin
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
```

```ShellSession
#Еще немного работы с репо
$ git pull origin master #Извлекли данные с удаленного сервера и слили их с текущей работой. Была выдана ошибка следующего характера: fatal: Couldn't find remote ref to
$ git log #Просмотр changelog'a
```

```ShellSession
#Создание каталогов и создание и запись файлов
$ mkdir sources #Создали каталог sources
$ mkdir include #Создали каталог include
$ mkdir examples #Создали каталог examples
$ cat > sources/print.cpp <<EOF #Создаем файл print.cpp в папке sources, заполняем его следующим кодом, оканчивающимся EOF - end of file
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF
```

```ShellSession
#Cоздание и запись файлов
$ cat > include/print.hpp <<EOF #Создаем файл print.hpp в папке sources, заполняем его следующим кодом, оканчивающимся EOF - end of file
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF
```

```ShellSession
#Cоздание и запись файлов
$ cat > examples/example1.cpp <<EOF #Создаем файл example1.cpp в папке sources, заполняем его следующим кодом, оканчивающимся EOF - end of file
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```

```ShellSession
#Cоздание и запись файлов
$ cat > examples/example2.cpp <<EOF #Создаем файл example2.cpp в папке sources, заполняем его следующим кодом, оканчивающимся EOF - end of file
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```

```ShellSession
#Редактирование
$ edit README.md #Редактирование файла README.md
```

```ShellSession
#Завершение работы
$ git status #Проверка статуса
$ git add . #Начало остлеживания версионного изменения для текущей директории
$ git commit -m"added sources" #Закоммитили изменения
$ git push origin master #Отправили ветку master на сервер origin
``` 

## Report

```ShellSession
$ cd ~/workspace/labs/ #Переходим в каталог
$ export LAB_NUMBER=03 #Задаем значение для LAB_NUMBER равное '03'
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER} #Копируем репо с удаленного сервера
$ mkdir reports/lab${LAB_NUMBER} #Создаем каталог
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md #Копируем файл README.md
$ cd reports/lab${LAB_NUMBER} #Переходим в каталог
$ edit REPORT.md #Редактируем файл
$ gistup -m "lab${LAB_NUMBER}" #Загуржаем файлы текущей директории в gist
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```

