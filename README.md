# Лабораторная работа №2 
## Часть 1
1) Создаю удаленный репозиторий <br />
2) Создаю локальный репозиторий <br />
3) Создаю файл  <br />
touch hello_world.cpp #include <iostream><br />
	Реализую программу:
	```
	using namespace std;
	int main() 
	{
	  cout << "Hello, World" << endl;
	  return 0;
	}
	```
  4) Добавляю этот файл в локальную копию репозитория: <br />
  git add h*
  5) Закомичу изменения: <br />
  git commit -m "added hello_world.cpp"
  6) Отредактирую файл hello_world.cpp:
	```
	#include <iostream>
	using namespace std;
	int main() {
	  string name;
	  cout << "Enter your name"; 
	  cin << name;
	  cout << "Hello World from " << name << endl;
	  return 0;
	}
	```
7) Закоммичу новую версию программы: <br />
git commit -am "added name"
8) Запушу изменения в удалённый репозиторий: <br />
git push -u origin master<br />
9)Проверю, что история коммитов доступна в удалённом репозитории
## Часть 2
1) В локальной копии репозитория создам ветку patch1 и перейду в неё: <br />
git checkout -b patch1
2) Отредактирую файл hello_world.cpp: 
	```
	#include <iostream>
	int main() {
	  string name;
	  cout << "Enter your name"; 
	  cin << name;
	  cout << "Hello World from " << name << endl;
	  return 0;
	}
	```
  3) Закоммичу изменения: <br />
  $ git commit -am "removed using namespace std line" <br />
	Запишу изменения в удаленный репозиторий:<br />
	$ git push -u origin HEAD
  4) Проверю, что ветка доступна в удаленном репозитории
  5) Создам PR patch1 -> master
6. В локальном репозитории, находясь в ветке patch1, отредактирую файл hello_world.cpp:
	```
	#include <iostream>
	using  namespace std;
	int main() {
	  string name;
	  cout << "Enter your name"; 
	  cin << name;
	  cout << "Hello World from " << name << endl;
	  return 0;
	}
	// комментарий:) 
	```
7. Закомичу изменения:<br />
	$ git commit -am "added comment"<br />
	Запишу изменения в удаленный репозиторий:<br />
	$ git push -u origin HEAD
8. Проверю, что новые изменения есть в созданном на шаге 5 pull-request
9. Выполню в удаленном репозитории слияние PR patch1 -> master и удалю ветку patch1 в удаленном репозитории
10. Выполню **pull** в локальном репозитории:<br />
	$ git pull<br />
11. Посмотрю историю в локальной версиит ветки:<br />
	$ git log --oneline --graph --decorate --all
12. Удалю локальную ветку patch1:<br />
	$ git checkout master<br />
	$ git pull<br />
	$ git branch -d patch1	

## Часть 3

1. Создам новую локальную ветку patch2
2. Скачаю пакет **clang-format**:<br />
	sudo apt install clang-format<br />
	Изменю *code style*:<br />
	clang-format -style=Mozilla /home/etosneks/lab02/hello_world.cpp
3. Закомичу изменения:<br />
	$ git commit -am "changed code style"<br />
	Запишу изменения в удаленный репозиторий:<br />
	$ git push -u origin HEAD
	Создам PR patch2 -> master
4. В удаленном репозитории в ветке **master** изменю комментарий:<br />
	> //комментарий:) -> //комментарий!!!
5. Проверю, что в pull-request появились конфликты
6. $ git pull <br />
	$ git rebase master
7. Сделаю *force push* в ветку patch2:<br />
	$ git push origin patch2 --force
8. Проверю, что в PR пропали конфликты
9. Вмержу PR patch2 -> master
