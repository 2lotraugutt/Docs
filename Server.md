# Grupy:
## sysadmin 
Upoważnia do pełnej administracji systemem
```sh
%sysadmin    ALL:(ALL:ALL)ALL
```
## webadmin 
Upoważnia do wszystkich komend jako urzytkownik "server" oraz do zrestartowania httpd (`sudo systemctl restart httpd.servece`)
```sh
%webadmin    ALL=NOEXEC: /user/bin/systemctl restart httpd.service
%webadmin    ALL=(server) ALL
```

# Użytkownicy
- **franek** - konto sysadmin dla Franciszka Skuta, automatycznie deaktywowane `2026-06-30`
- **bartek** - konto webadmin dla Bartosza Wiaderka, automatycznie deaktywowane `2026-06-30`
- **konrad** - konto sysadmin dla Konrada Woszczyka, dezaktywowane manualnie
- **server** - konto uruchamiające server nextjs przez `/etc/systemd/system/httpd.service`
- **postgres** - konto służące do administracji bazą danych postgresql

# Usługi
- `/etc/systemd/system/httpd.service`
```sh
[Unit]
After=network.target

[Service]
User=server
ExecStart=/home/server/Traugut.net/node_modules/.bin/next start -p 8888
```