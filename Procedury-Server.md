# Zarządzanie użytkownikami
## Dodawanie użytkownika 
```sh
sudo adduser {nazwa użytkownika}
sudo adduser {nazwa użytkownika} {webadmin, sysadmin}
```
**WAŻNE**: Ustawić date wygaśnięcia użytkownika!
## Usuwanie użytkownika
```sh
sudo deluser {nazwa użytkownika}
```
## Ustawianie daty wygaśnięcia dla użytkownika
```sh
sudo chage -E {data wygaśniecia} {nazwa użytkownika}
```
## 
