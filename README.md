# Laboratorium 3
Zad.8 Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach. 

ODP. head -n 0 /etc/* | tr -s '[n*2]' 'n' | wc -l
