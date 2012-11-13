#Laboratorium 1
Zad.1 Używając linii poleceń stwórz strukturę katalogów:

temp
|-- dom
|-- nauka
|   |-- c
|   |-- logo
|   `-- pascal
`-- praca
    |-- dokumenty
    `-- zlecenia
        |-- niezrealizowane
        `-- zrealizowane
```sh
ODP. mkdir -p temp/dom
     mkdir -p temp/nauka/{c,logo,pascal}
     mkdir -p temp/praca/{dokumenty,zlecenia}
     mkdir -p temp/praca/zlecenia/{niezrealizowane,zrealizowane}
     cd temp | tree
```

Zad.2 Przejdź do katalogu dom i utwórz katalog wazne-sprawy.
```sh
ODP. cd dom
     mkdir wazne-sprawy
```

Zad.3 Wejdź do katalogu wazne-sprawy i utwórz tam pusty plik rachunki.txt.
```sh
ODP. cd wazne-sprawy
     touch rachunki.txt
```

Zad.4 Będąc w katalogu wazne-sprawy skopiuj plik rachunki.txt do katalogu zrealizowane.
```sh
ODP. cp rachunki.txt ../../praca/zlecenia/zrealizowane/rachunki.txt
```

Zad.5 Przejdź do katalogu zrealizowane i zmień nazwę pliku rachunki.txt na wykonano.txt.
```sh
ODP. cd ../..
     cd praca/zlecenia/zrealizowane
     mv rachunki.txt wykonano.txt
```
Polecenia: split, cat, diff

Zad.6 Utwórz plik wykonano.txt wielkości 11 bajtów, następnie podziel go pliki wielkości 5 bajtów. W ten sposób otrzymasz 3 pliki. (split)
```sh
ODP. cat > wykonano.txt 
    12345678901 (potem wcisnąć Ctrl+D)
    split -b 5 wykonano.txt
```

Zad.7 Będąc w katalogu logo skopiuj powyżej otrzymane 3 pliki do katalogu dokumenty.
```sh
ODP. cp ../../praca/zlecenia/zrealizowane/x* ../../praca/dokumenty
```

Zad.8 Będąc w katalogu dokumenty połącz skopiowane 3 pliki w plik odtworzono.txt, tak aby otrzymać plik o zawartości identycznej z wykonano.txt. Następnie plik odtworzono.txt skopiuj do katalogu wazne-sprawy.
```sh
ODP. cat xaa xab xac > odtworzono.txt
     cp odtworzono.txt ../../dom/wazne-sprawy/odtworzono.txt
```

Zad.9 Będąc w katalogu wazne-sprawy sprawdź, czy są jakieś różnice w zawartości plików wykonano.txt i odtworzono.txt.
```sh
ODP. diff -a ../../praca/zlecenia/zrealizowane/wykonano.txt odtworzono.txt
```

Zad.10 Wyświetl kalendarz na październik 2009 r. (cal)
```sh
ODP. cal 10 2009
```
Wyświetl kalendarz na wrzesień, październik i listopad 2009 r. z miesiącami obok siebie (cal):
```sh
ODP. cal -3 2009
```

Zad.11 Jaki był dzień tygodnia 25 maja 1975 r. (cal i date)
```sh
ODP. date -d 1975-05-25 +%A
```

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
ODP. grep "main" program.c
```

Zad.4 Plikowi program.c nadaj następujące uprawnienia: właściciel – czytanie, pisanie, grupa – czytanie, pozostali użytkownicy: brak uprawnień. (chmod)
```sh
ODP. chmod 650 program.c
```

Zad.5 Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca.
```sh
ODP. mv dom/wazne-sprawy praca/wazne-sprawy
```

Zad.6 Zarchiwizuj cały katalog temp. (zip i tar)
```sh
ODP. tar -cvf temp.tar temp
     gzip temp.tar
```

Zad.7 Usuń katalog temp.
```sh
ODP. rm -rf temp
```

Zad.8 Odtwórz z archiwum katalog temp. (unzip i tar)
```sh
ODP. tar -zxf temp.tar.gz
```

Zad.9 Posprzątaj na swoim koncie.
```sh
ODP. cd ~/tmp
     rm -rf *
```

# Laboratorium 3
Zad.1 Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu.
```sh
ODP. more -5 /etc/passwd
```

Zad.2 Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt.
```sh
ODP. cat tekst1.txt - tekst2.txt > tekst3.txt
```
lub
```sh
ODP. cat tekst1.txt > tekst3.txt
     cat >> tekst3.txt
     cat tekst2.txt >> tekst3.txt
```


Zad.3 Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób, aby nie były wyświetlane ich nazwy.
```sh
ODP. head home/* -n 5 -q
```
lub
```sh
ODP. head -qn 5 *
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
ODP. find /etc -type f 2> dev/null/ wc -l
```
lub
```sh
ODP. find /etc -type f 2> errors | wc -l
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
lub
```sh
ODP. head /etc/passwd -n 3 | wc -c
```


# Laboratorium 4
Zad.1 Wyświetl listę plików z aktualnego katalogu, zamieniając wszystkie małe litery na duże.
```sh
ODP. ls | tr [:lower:] [:upper:] (nie obsługuje znaków narodowych)
```
lub
```sh
ODP. ls | tr a-z A-Z
```
dla polskich liter
```sh
ODP. ls | tr [:lower:]ąęćłśżź [:upper:]ĄĘŁŚŻŹ
```

Zad.2 Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
```sh
ODP. ls -l | awk '{print $1,$5,$9}'
```
lub
```sh
ODP. find . -type f -exec ls -l '{}' ';' | cut -d ' ' -f1,5,9
```
lub
```sh
ODP. ls --format=long --human-readable
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
ODP. find . -maxdepth 1 -not - type d -exec ls -l '{}' ';' | sort -n -t ' ' -k6,6
```  
lub
```sh
ODP. ls --sort=size -1
```

Zad.4 Wyświetl zawartość pliku /etc/passwd posortowaną według numerów UID w kolejności od największego do najmniejszego.
```sh
ODP. cat /etc/passwd | sort -n -t ':' -k3,3
```
lub
```sh
ODP. sort -t : -n -k3 -r /etc/passwd
```
lub
```sh
ODP. cat /etc/passwd | sort -r -t: -g -k 3
```
lub
```sh
ODP. sort -t : -k3 -nr
```

Zad.5 Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
```sh
ODP. sort -t : -k4 -r /etc/passwd | sort -t : -k3 
```
lub
```sh
ODP. cat /etc/passwd | sort --field-separator=":" 
```

Zad.6 Podaj liczbę plików każdego użytkownika.
```sh
ODP. find $HOME -not -type d| wc -l
```

Zad.7 Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
```sh
ODP. find -printf "%m\n" | sort | uniq -c
```

Efekt wykonania poniższych poleceń?

1) ls -l > lsout.txt 
```sh
ODP. Utwotrzenie pliku lsout.txt i wypelnienie jej lista plikow w akutalnym katalogu
```
2) ls -la >> lsout.txt
```sh
ODP. Dopisuje do pliku lsout.txt liste uruchomionych procesów
```
3) ps >> psout.txt
```sh
ODP. Dopisuje ilosc wolnej pamięci
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

#Laboratorium 6
Zad.1 W pliku plik.txt znajdź wiersze zawierające co najmniej jeden znak.
```sh
ODP. grep . {1,} plik.txt
```

Zad.2 Znajdź w plikach pl* wiersze rozpoczynające się od cyfry.
```sh
ODP. grep ^[0-9] pl*
```

Zad.3 Znajdź pliki, zawierające wiersz w którym na 9 pozycji występuje litera r.
```sh
ODP. ls -1 | grep -E '^.{8}r.*'
```

Zad.4 Policz, ilu użytkowników systemu używa powłoki bash (zgodnie z zapisami w pliku /etc/passwd).
```sh
ODP. grep -c bash /etc/passwd
```

Zad.5 Znajdź wiersze zawierające liczby rzymskie w pliku plik.txt.
```sh
ODP.  egrep "(X|D|C|M|V|L|I){1,}" plik.txt
```

