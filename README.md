#Laboratorium 2
Zad.1 Wyświetl na ekran 2 pierwsze wiersze pliku program.c. (head)
```sh
ODP. head -n 2 program.c
```

Zad.2 Wyświetl na ekran 4 ostatnie wiersze pliku program.c. (head,tail)
```sh
ODP. tail -n 4 program.c
```

Zad.3 W pliku program.c znajdź wszystkie wiersze z wystąpieniem słowa „main”. (grep)
```sh
ODP. grep -n main
```

Zad.4 Plikowi program.c nadaj następujące uprawnienia: właściciel – czytanie, pisanie, grupa – czytanie, pozostali użytkownicy: brak uprawnień. (chmod)
```sh
ODP. chmod 540 program.c
```

Zad.5 Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca.
```sh
ODP. mv ~/temp/dom/wazne-sprawy ~/temp/praca/
```

Zad.6 Zarchiwizuj cały katalog temp. (zip i tar)
```sh
ODP. tar cvf temp.tar 
     zip zvf temp.zip
```

Zad.7 Usuń katalog temp.
```sh
ODP. rmdir temp
```

Zad.8 Odtwórz z archiwum katalog temp. (unzip i tar)
```sh
ODP. tar zxf temp.tar
     unzip zxf temp.zip
```

Zad.9 Posprzątaj na swoim koncie.

# Laboratorium 3
Zad.1 Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu.
```sh
ODP. more -5 /etc/passwd
```

Zad.2 Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt.
```sh
ODP. cat tekst1.txt - tekst2.txt > tekst3.txt
```

Zad.3 Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób, aby nie były wyświetlane ich nazwy.
```sh
ODP. head home/* -n 5 -q
```

Zad.4 Wyświetl linie o numerach 3, 4 i 5 z pliku /etc/passwd.
```sh
ODP. head -n 5 /etc/passwd | tail -n 3
```

Zad.5 Wyświetl linie o numerach 7, 6 i 5 od końca pliku /etc/passwd.
```sh
ODP. tail -n 7 /etc/passwd | head -n 3 
```

Zad.6 Wyświetl zawartość pliku /etc/passwd w jednej linii.
```sh
ODP. cat /etc/passwd |tr "n" " "
```

Zad.7 Za pomocą filtru tr wykonaj modyfikację pliku plik.txt, polegającą na umieszczeniu każdego słowa w osobnej linii.
```sh
ODP. cat plik.txt | tr " \t" "\n"
```

Zad.8 Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach. 
```sh
ODP. find /etc -type f -follow | wc -1
```

Zad.9 Napisać polecenie zliczające ilość znaków z pierwszych trzech linii pliku /etc/passwd.
```sh
ODP. find /etc/ | head -3 | wc | tr '''\n' | tail -1
```
lub
```sh
ODP. find /etc/ | head -3 | wc -c
```
lub
```sh
ODP. cat /etc/passwd/ | head -n 3 | wc -m
```

# Laboratorium 4
Zad.1 Wyświetl listę plików z aktualnego katalogu, zamieniając wszystkie małe litery na duże.
```sh
ODP. ls | tr [:lower:] [:upper:]
```
lub
```sh
ODP. ls | tr '[a-z]' '[A-Z]'
```

Zad.2 Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
```sh
ODP. ls -l | awk '{print $1,$5,$9}'
```
lub
```sh
ODP. find . -not -type d -maxdepth 1
   -exec ls -l '{}' ';' | cut -d ' ' -f1,6,9
```

Zad.3 Wyświetl listę plików w aktualnym katalogu, posortowaną według rozmiaru pliku.
```sh
ODP. ls -l | sort -k5,5
```
lub
```sh
ODP. ls -lrS
```
lub
```sh
ODP. find . -maxdepth 1 -not - type d -exec ls -l '{}' ';' 
  | sort -n -t ' ' -k6,6
```  

Zad.4 Wyświetl zawartość pliku /etc/passwd posortowaną według numerów UID w kolejności od największego do najmniejszego.
```sh
ODP. cat /etc/passwd | sort -n -t ':' -k3,3
```
lub
```sh
ODP. sort -t : -n -k3 -r /etc/passwd
```

Zad.5 Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
```sh
ODP. sort -t : -k4 -r /etc/passwd | sort -t : -k3 
```

Zad.6 Podaj liczbę plików każdego użytkownika.
```sh
ODP. find $HOME -not -type d| wc -l
```

Zad.7 Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
```sh
ODP. 
```

#Laboratorium 5
Zad.1 Znajdź w swoim katalogu domowym (bez podkatalogów) wszystkie pliki, które zostały zmodyfikowane w ciągu ostatnich dziesięciu dni i wyświetl ich nazwy.
```sh
ODP. find ~/ -maxdepth 1 -mtime -10
```

Zad.2 Znajdź wszystkie pliki zwykłe w systemie, które mają w nazwie ciąg znaków „conf” i wyświetl ich nazwy na ekranie.
```sh
ODP. find  / -name \*config\* -type f 2> /dev/null
```

Zad.3 Znajdź w swoim katalogu domowym wszystkie pliki, które nie były używane w ciągu ostatnich 20 dni.
```sh
ODP. find ~/ -atime 20
```

Zad.4 Znajdź w katalogu /etc wszystkie niepuste podkatalogi i pliki o nazwach zaczynających się na literę „a”.
```sh
ODP. find /etc \( -type f -and -name a* \) -or \( -type d -and ! -empty \) 2> /dev/null
```

Zadania różne

Zad.5 Z bieżącego katalogu usuń pliki, których nazwa zaczyna się na literę „x” i zawiera dokładnie trzy znaki.
```sh
ODP. rm x??
```

Zad.6 Skonstruuj polecenie tworzące katalog, którego nazwą będzie aktualna (w momencie wywołania) systemowa data w formacie rrrr-mm-dd.
```sh
ODP. mkdir date +%Y-%m-%d
```


