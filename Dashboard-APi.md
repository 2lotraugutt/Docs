# Dashboard API
> API serwera (wymagające weryfikacji) znajduje się w folderze: `/app/api/dashboard/`

# Lista:
- [`account/`](#account)
- [`calednar/`](#calednar)
- [`notifications/`](#notifications)
- [`posts/`](#posts)
- [`roles/`](#roles)
- [`users/`](#users)


# Ścieżki:
## `account/`
> Możliwe zapytania - GET, POST

Przykładowy request:
```
/api/dashboard/account
```

> #### Metoda: GET
> Funkcja zwraca dane aktualnie zalogowanego użytkownika.

Przykładowy Dane:
```JSON
{
  "id": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "email": "bartoszwiaderek@gmail.com",
  "emailVerified": null,
  "name": "Bartosz Wiaderek",
  "image": "https://lh3.googleusercontent.com/a/AAcHTte0zfu0POREtU6vPYSC8Na2Ox3NKUUGTSkqMVGhNBIB9oU=s96-c",
  "verified": true,
  "roleTag": "ADMIN",
  "role": {
    "tag": "ADMIN",
    "name": "Administrator",
    "createPosts": true,
    "publishPosts": true,
    "managePosts": true,
    "manageUsers": true,
    "verifyUsers": true,
    "manageEvents": true,
    "manageCalendar": true,
    "manageRoles": true,
    "manageNotifications": true
  }
}
```
***
> #### Metoda: POST
> Funkcja zmienia imie (`name`) uytkownika w bazie danej

Body zapytania **(wymagane)**:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| name      | string | 
## `calednar/`
## `notifications/`
> Możliwe zapytania - GET, POST, PUT, DELETE

> #### Metoda: GET
> Funkcja zwraca wybraną ilość wiadomości, wraz z autorem, który je stworzył
> 
> Wymagane persmisje: `manageNotifications`


Argumenty (opcjonalne):
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| count      |CYFRA | 

Przykładowy request:
```
/api/dashboard/notifications?count=1
```

Przykładowy Dane:
```JSON
[{
  "id": "ff9af896-d336-46da-a0be-5771bc29197d",
  "createdAt": "2023-09-01T15:47:33.000Z",
  "title": "Zebrania z rodzicami",
  "content": "Szanowni PaÅ„stwo\r\nDyrekcja szkoÅ‚y informuje, Å¼e we wtorek 5.09.2023r o godz. 18.00 odbÄ™dÄ… siÄ™ zebrania z rodzicami uczniÃ³w klas I.\r\n\r\nRozpocznÄ… siÄ™ od spotkania z Dyrektorem szkoÅ‚y w duÅ¼ej sali gimnastycznej, a nastÄ™pnie z wychowawcami w salach lekcyjnych.\r\n\r\nW nastÄ™pny wtorek tj. 12.09.2023r. rÃ³wnieÅ¼ o godz. 18:00 odbÄ™dÄ… siÄ™ zebrania wychowawcÃ³w z rodzicami uczniÃ³w klas II, III i IV.",
  "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "author": {
    "id": "82c50b88-97fb-46c3-8e85-222d83192b19",
    "email": "bartoszwiaderek@gmail.com",
    "emailVerified": null,
    "name": "Bartosz Wiaderek",
    "image": "https://lh3.googleusercontent.com/a/AAcHTte0zfu0POREtU6vPYSC8Na2Ox3NKUUGTSkqMVGhNBIB9oU=s96-c",
    "verified": true,
    "roleTag": "ADMIN"
    }
}]
```

***
> #### Metoda: POST
> Funkcja tworzy nową wiadomość w bazie danych. Jako autora przyjmuje osobę aktualnie zalogowaną.
> 
> Wymagane persmisje: `manageNotifications`

Body zapytania **(wymagane)**:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| title      |string | 
| content      | string | 

Przykładowy request:
```
/api/dashboard/notifications
```
***
> #### Metoda: PUT
> Funkcja edytuje dane postu. Jego tytuł (`title`) i treść (`content`). Post wyszukiwany jest po `id`.
> 
> Wymagane persmisje: `manageNotifications`

Body zapytania **(wymagane)**:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| id      |ID Posta | 
| title      |string | 
| content      | string | 

Przykładowy request:
```
/api/dashboard/notifications
```
***
> #### Metoda: DELETE
> Funkcja usuwa post którego `id` zgode jest z tym podanych w body.
> 
> Wymagane persmisje: `manageNotifications`

Body zapytania **(wymagane)**:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| id      |ID Posta | 

Przykładowy request:
```
/api/dashboard/notifications
```
## `posts/`
## `roles/`
## `users/`
