# Laboratorium 3
Zad.1 Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu.

```sh
ODP. more -5 /etc/passwd
```

Zad.8 Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach. 

```sh
ODP. head -n 0 /etc/* | tr -s '[n*2]' 'n' | wc -l
```