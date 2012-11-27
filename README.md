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
lub
```sh
ODP. cal 11 2009 -3m
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
lub
```sh
ODP. chmod u+rw program.c
     chmod g+r program.c
     chmod o-rwx program.c
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
lub
```sh
ODP. zip -r temp.zip temp
```

Zad.7 Usuń katalog temp.
```sh
ODP. rm -rf temp
```
lub
```sh
ODP. rm -R temp
```

Zad.8 Odtwórz z archiwum katalog temp. (unzip i tar)
```sh
ODP. tar -zxf temp.tar.gz
     unzip temp.zip
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
ODP. head $HOME/* -n 5 -q
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
ODP. cat /etc/passwd | tr "n" " "
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
lub
```sh
ODP. find /etc -type f -follow | wc -l
```
lub
```sh
ODP. head -n 0 /etc/* | tr -s '[n*2]' 'n' | wc -l
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
lub
```sh
ODP. cut /etc/passwd | head -n 3 | wc -n
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
dla polskich liter:
```sh
ODP. ls | tr [:lower:]ąęćłśżź [:upper:]ĄĘŁŚŻŹ
```

Zad.2 Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
```sh
ODP. ls -l | awk '{print $1,$5,$9}'
```
lub
```sh
ODP. find . -type f -exec ls -l '{}' ';' | cut -d ' ' -f1,5,9 (nie działa dla plików z datami dwucyfrowymi)
```
lub
```sh
ODP. ls --format=long --human-readable
```
lub
```sh
ODP. find . -printf "Plik: %f Rozmiar: %s Prawa: %M \n" -maxdepth 1
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
ODP. sort -t : -k3 -nr /etc/passwd
```
lub
```sh
ODP. cat /etc/passwd/ | sort --reverse --general-numeric-sort
```

Zad.5 Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
```sh
ODP. sort -t : -k4 -r /etc/passwd | sort -t : -k3 
```
lub
```sh
ODP. cat /etc/passwd | sort --field-separator=":" 
```
lub
```sh
ODP. cat /etc/passwd | sort -r --field-separator=":" -g -k 4,3
```

Zad.6 Podaj liczbę plików każdego użytkownika.
```sh
ODP. find $HOME -not -type d | wc -l
```
lub
```sh
ODP. find / -printf "%u\n" 2> /dev/null | sort | uniq -c
```

Zad.7 Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
```sh
ODP. find -printf "%m\n" | sort | uniq -c
```

Zad.8 Efekt wykonania poniższych poleceń?

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
ODP. find ~/ -maxdepth 1 -mtime -10 -type f (maxdepth podać pierwsze w kolejności)
```

Zad.2 Znajdź wszystkie pliki zwykłe w systemie, które mają w nazwie ciąg znaków „conf” i wyświetl ich nazwy na ekranie.
```sh
ODP. find  /etc -name \*config\* -type f 2> /dev/null
```

Zad.3 Znajdź w swoim katalogu domowym wszystkie pliki, które nie były używane w ciągu ostatnich 20 dni.
```sh
ODP. find ~/ \( -type d -name ".git" -prune \) -o \( -type f -print \) 
```
lub
```sh
ODP. find ~/ -atime 20 (nie do końca)
```
lub 
```sh 
ODP. find . -path '*/.git/*' - prune -o -print
```
lub
```sh
ODP. -mtime -20 | egrep -v '/\.git' (praktyczniejsza wersja z mtime)
```
lub
```sh
ODP. find . ! -regex ".*/\.git/?.*"
```

Zad.4 Znajdź w katalogu /etc wszystkie niepuste podkatalogi i pliki o nazwach zaczynających się na literę „a”.
```sh
ODP. find /etc \( -type f -and -name a* \) -or \( -type d -and ! -empty \) 2> /dev/null (nie działa do niektórych katalogów)
```
lub
```sh
ODP. find /etc\(-type d -and ! empty\) -or \(-type f -and -name a*\) 2> /dev/null
```

Zadania różne

Zad.5 Z bieżącego katalogu usuń pliki, których nazwa zaczyna się na literę „x” i zawiera dokładnie trzy znaki.
```sh
ODP. rm x?? (dotyczy bieżącego katalogu)
```
lub
```sh
ODP. find. -minidepth 2 -maxdepth 2 -name x?? -exec rm -rf \(\) \;
```
lub 
```sh
ODP. find. -minidepth 2 -maxdepth 2 -name x?? -delete (jest krótsze)

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
ODP. egrep "(X|D|C|M|V|L|I){1,}" plik.txt
```

#Laboratorium 7
Zad.1 W bieżącym katalogu zamienić rozszerzenia wszystkich plików z rozszerzeniem htm na html. Jeżeli w nazwie pliku istnieje spacja, to należy zamienić ją na znak podkreślenia.
```sh
ODP. #!/bin/bash

     for plik1 in *.htm
     do
       plik2=`echo "$plik1"l | tr " " "_"`
       mv "$plik1"  "$plik2"

     done
     exit 0
```

Zad.2 Napisać skrypt zawierający funkcję obliczającą silnię. Następnie należy obliczyć silnię z liczby, która jest argumentem skryptu. W przypadku niepoprawnego argumentu należy wypisać odpowiedni komunikat.
```sh
ODP. #!/bin/bash
     if [ $# -eq 0 ]
     then
       echo "Wpisz: bash $0 liczba_naturalna"
       exit 1
     fi
     silnia=1
     for (( i=1; i<=$1; i++ ))
     do
       silnia=`expr $silnia \* $i`
     done
     echo "Silnia z liczby $1 = $silnia"
     exit 0
```

Zad.3 Napisać skrypt zbierający jak najwięcej informacji o użytkowniku, którego login jest argumentem skryptu. Jeżeli skrypt nie ma argumentu, to należy użyć login osoby uruchamiającej skrypt.
```sh
ODP. if [ $# -ge 1 ];
     then
         user=$1
     else
         user=`whoami`
     fi
     id $user 2> /dev/null > /dev/null
     if [ $? -eq 0 ];
     then
         echo "Uzytkownik nazywa sie $user"
         users | grep -w "$user" > /dev/null 2> /dev/null
         if [ $? -eq 0 ];
         then
         echo "Jest aktualnie zalogowany"
         else
         echo "Nie jest aktualnie zalogowany"
         fi
         echo "Nalezy do grup: "`id $user -gn`
         user_passwd=`cat /etc/passwd | grep -w $user`
         if [ $? -eq 0 ];
         then
         home_dir=`echo $user_passwd | cut -d ":" -f 6`
         shell=`echo $user_passwd | cut -d ":" -f 7`
         echo "Katalog domowy to $home_dir a powloka jakiej uzywa to $shell"
         else
         echo "W pliku /etc/passwd nie ma informacji o tym uzytkowniku"
         fi
     else
         echo "Uzytkownik $user nie istnieje"
     fi
```

Zad.4 Napisz skrypt usuwający z katalogu domowego i jego podkatalogów wszystkie pliki zwykłe o nazwie 'core' starsze niż 3 dni.
```sh
ODP. #!/bin/bash

     elif=`find ~ -name "core" -ctime +3  -type f`
     rm "$elif"
     echo "Zrobione"
     exit 0
