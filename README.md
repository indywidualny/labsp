# Laboratorium 3
Zad.1 Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu.

```sh
ODP. more -5 /etc/passwd
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