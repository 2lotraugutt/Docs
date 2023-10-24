# Public API
> API serwera (ogólnodostępne) znajduje się w folderze: `/app/api/`

# Lista:
- [`auth/[...nextAuth]` - ścieka wykorzystywana przez NextAuth przy logowaniu, itd.](#authnextauth---ścieka-wykorzystywana-przez-nextauth-przy-logowaniu-itd)
- [`calendar/`](#calendar)
  - [`calendar/days/` - zwraca wybrane obiekty dnia wraz z wydarzeniami oraz tagami](#calendardays---zwraca-wybrane-obiekty-dnia-wraz-z-wydarzeniami-oraz-tagami)
  - [`calendar/events/` - zwraca wybrane obiekty wydarzeń wraz z tagami](#calendarevents---zwraca-wybrane-obiekty-wydarzeń-wraz-z-tagami)
  - [`calendar/getNumbers/` - zwraca wszystkie 'szcześliwe' numerki.](#calendargetnumbers---zwraca-wszystkie-szcześliwe-numerki)
  - [`calendar/getWeekNumbers/` - zwraca 'szcześliwe' numerki z bieżącego tygodnia](#calendargetweeknumbers---zwraca-szcześliwe-numerki-z-bieżącego-tygodnia)
- [`notifications/` - zwraca wybraną liczbe informacji](#notifications---zwraca-wybraną-liczbe-informacji)
- [`posts/` - zwraca wybraną ilość postów stworzonych przez wybraną osobę](#posts---zwraca-wybraną-ilość-postów-stworzonych-przez-wybraną-osobę)
  - [`posts/post/` - zwraca jeden, najnowszy post. Dane zwracane są wraz z autorem.](#postspost---zwraca-jeden-najnowszy-post-dane-zwracane-są-wraz-z-autorem)
  - [`posts/post/[id]` - zwraca jeden post według ID w argumencie. Dane zwracane są wraz z autorem.](#postspostid---zwraca-jeden-post-według-id-w-argumencie-dane-zwracane-są-wraz-z-autorem)
  - [`posts/post/views/[id]` - zwiększa ilość wyświetleń postu](#postspostviewsid---zwiększa-ilość-wyświetleń-postu)
  - [`posts/topPosts/` - zwraca najpopularniejsze posty sprzed 30 dni](#poststopposts---zwraca-najpopularniejsze-posty-sprzed-30-dni)


# Ścieżki:
## `auth/[...nextAuth]` - ścieka wykorzystywana przez NextAuth przy logowaniu, itd.
## `calendar/`
### `calendar/days/` - zwraca wybrane obiekty dnia wraz z wydarzeniami oraz tagami
> Możliwe zapytania - GET

Argumenty (opcjonalne):
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| year      |ROK | 
| month      | od 0 do 11      | 

Przykładowy request:
```
api/calendar/days?year=2023&month=9
```

Przykładowy Dane:
```JSON
[{
  "date": "20-10-2023",
  "number": 30,
  "freeDay": false,
  "day": 20,
  "month": 9,
  "year": 2023,
  "timeStamp": "2023-10-20T00:00:00.000Z",
  "events": [
    {
      "id": "ee3357c0-bf3f-411e-920d-7d000cf991c3",
      "createdAt": "2023-09-30T00:20:26.938Z",
      "name": "Wieczór filmowy",
      "description": "Tego dnia odbędzie się wieczór filmowy, seans rozpoczynamy o godzinie 19:00. ",
      "date": "20-10-2023",
      "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19",
      "tags": [
        {
          "id": "eadc2085-8fdb-4b7a-ba9f-525eced1b7c7",
          "createdAt": "2023-09-20T20:22:46.433Z",
          "name": "Na śmiesznie",
          "color": "#0FA3B1",
          "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19"
        }
      ]
    }
  ]
}]
```
### `calendar/events/` - zwraca wybrane obiekty wydarzeń wraz z tagami
> Możliwe zapytania - GET

Argumenty (opcjonalne):
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| count      |CYFRA | 

Body zapytania **(wymagane)**:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| year      |ROK | 
| month      | od 0 do 11      | 
| day | od 0 do 27-30     |  


Przykładowy request:
```
/api/calendar/events?count=1
```

Przykładowy Dane:
```JSON
[{
  "id": "ee3357c0-bf3f-411e-920d-7d000cf991c3",
  "createdAt": "2023-09-30T00:20:26.938Z",
  "name": "Wieczór filmowy",
  "description": "Tego dnia odbędzie się wieczór filmowy, seans rozpoczynamy o godzinie 19:00. ",
  "date": "20-10-2023",
  "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "tags": [
    {
      "id": "eadc2085-8fdb-4b7a-ba9f-525eced1b7c7",
      "createdAt": "2023-09-20T20:22:46.433Z",
      "name": "Na śmiesznie",
      "color": "#0FA3B1",
      "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19"
    }
  ]
}]
```
### `calendar/getNumbers/` - zwraca wszystkie 'szcześliwe' numerki.
> Możliwe zapytania - GET

Argumenty (opcjonalne):
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| year      |ROK | 
| month      | od 0 do 11      | 
| day | od 0 do 27-30     |   

Przykładowy request:
```
api/calendar/getNumbers?year=2023&month=9&day=20
```

Przykładowy Dane:
```JSON
[{
  "number": 24,
  "date": "20-10-2023"
}]
```
### `calendar/getWeekNumbers/` - zwraca 'szcześliwe' numerki z bieżącego tygodnia
> Możliwe zapytania - GET

Przykładowy request:
```
api/calendar/getWeekNumbers
```

Przykładowy Dane:
```JSON
[{
  "number": 18,
  "date": "23-10-2023"
},
{
  "number": 24,
  "date": "24-10-2023"
},
{
  "number": 28,
  "date": "25-10-2023"
},
{
  "number": 1,
  "date": "26-10-2023"
},
{
  "number": 10,
  "date": "27-10-2023"
}]
```
## `notifications/` - zwraca wybraną liczbe informacji
> Możliwe zapytania - GET

Argumenty (opcjonalne):
| Argument      | Wartości           | 
| ------------- |:-------------:| 
| count      |CYFRA | 

Przykładowy request:
```
/api/notifications?count=2
```

Przykładowy Dane:
```JSON
[{
  "id": "ff9af896-d336-46da-a0be-5771bc29197d",
  "createdAt": "2023-09-01T15:47:33.000Z",
  "title": "Zebrania z rodzicami",
  "content": "Szanowni Państwo\r\nDyrekcja szkoły informuje, że we wtorek 5.09.2023r o godz. 18.00 odbędą się zebrania z rodzicami uczniów klas I.\r\n\r\nRozpoczną się od spotkania z Dyrektorem szkoły w dużej sali gimnastycznej, a następnie z wychowawcami w salach lekcyjnych.\r\n\r\nW następny wtorek tj. 12.09.2023r. również o godz. 18:00 odbędą się zebrania wychowawców z rodzicami uczniów klas II, III i IV.",
  "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19"
},
{
  "id": "ff5f4f17-1287-4dcf-a25c-5229b3348a1a",
  "createdAt": "2023-09-01T08:00:21.000Z",
  "title": "Rozpoczęcie roku szkolnego 2023/2024",
  "content": "Uroczyste rozpoczęcie roku szkolnego 2023/2024 odbędzie się 4 września 2023 w dużej sali gimnastycznej:\r\n\r\n- o godzinie 9.00- dla klas II , III , IV\r\n- o godzinie 11.00- dla klas I",
  "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19"
}]
```
## `posts/` - zwraca wybraną ilość postów stworzonych przez wybraną osobę
> Możliwe zapytania - GET

Argumenty (opcjonalne):
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| count      |CYFRA | 
| author      |ID AUTORA | 

Przykładowy request:
```
/api/posts?count=1&author=82c50b88-97fb-46c3-8e85-222d83192b19
```

Przykładowy Dane:
```JSON
[{
  "id": "aa4746b4-4e3e-48aa-9674-91ec4377f7a1",
  "createdAt": "2023-05-19T00:00:00.000Z",
  "title": "Test kompetencji językowych",
  "content": "# Oddział Międzynarodowy w II LO im. Romualda Traugutta w Częstochowie\r\nZakres materiału gramatycznego i leksykalnego z języka angielskiego obowiązujący na części pisemnej sprawdzianu kompetencji językowych\r\n### Materiał gramatyczny oraz leksykalny.",
  "published": true,
  "views": 3,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "publishedById": "28105da3-ece4-43e3-90a8-ba7b1e52de82"
}]
```
### `posts/post/` - zwraca jeden, najnowszy post. Dane zwracane są wraz z autorem.
> Możliwe zapytania - GET

> Funkcja sprawdza czy post jest opublikowany.
> - Jeżeli tak: zwyczajnie zwraca dane.
> - Jeżeli nie: sprawdza czy osoba fetch'ująca jest właścicielem.
>   - Jeżeli tak: zwraca dane.
>   - Jeżeli nie: zwraca pusty objekt: `{}`

Przykładowy request:
```
api/posts/post/
```

Przykładowy Dane:
```JSON
{
  "id": "21228c32-f966-480f-9c1c-af3faf4aaf83",
  "createdAt": "2023-06-06T00:00:00.000Z",
  "title": "Konsultacje z rodzicami:",
  "content": "06.06.2023r (wtorek) w godz. 18.00-19.00 odbędą się konsultacje dla rodziców. Dyrekcja szkoły",
  "published": true,
  "views": 27,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
  "publishedById": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "author": {
    "id": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
    "email": "Archiwum",
    "emailVerified": null,
    "name": "Archiuwm",
    "image": "/Archiwum.png",
    "verified": true,
    "roleTag": "ADMIN"
  }
}
```
### `posts/post/[id]` - zwraca jeden post według ID w argumencie. Dane zwracane są wraz z autorem.
> Możliwe zapytania - GET

> Funkcja sprawdza czy post jest opublikowany.
> - Jeżeli tak: zwyczajnie zwraca dane.
> - Jeżeli nie: sprawdza czy osoba fetch'ująca jest właścicielem.
>   - Jeżeli tak: zwraca dane.
>   - Jeżeli nie: zwraca pusty objekt: `{}`

Argumenty (wymagane):
| Argument        | Wartości   |        
| ------------- |:-------------:| 
| id      | ID POSTU | 


Przykładowy request:
```
api/posts/post/21228c32-f966-480f-9c1c-af3faf4aaf83
```

Przykładowy Dane:
```JSON
{
  "id": "21228c32-f966-480f-9c1c-af3faf4aaf83",
  "createdAt": "2023-06-06T00:00:00.000Z",
  "title": "Konsultacje z rodzicami:",
  "content": "06.06.2023r (wtorek) w godz. 18.00-19.00 odbędą się konsultacje dla rodziców. Dyrekcja szkoły",
  "published": true,
  "views": 27,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
  "publishedById": "82c50b88-97fb-46c3-8e85-222d83192b19",
  "author": {
    "id": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
    "email": "Archiwum",
    "emailVerified": null,
    "name": "Archiuwm",
    "image": "/Archiwum.png",
    "verified": true,
    "roleTag": "ADMIN"
  }
}
```
### `posts/post/views/[id]` - zwiększa ilość wyświetleń postu
> Możliwe zapytania - GET

Argumenty (wymagane):
| Argument        | Wartości   |        
| ------------- |:-------------:| 
| id      | ID POSTU | 

Przykładowy request:
```
/api/posts/post/views/21228c32-f966-480f-9c1c-af3faf4aaf83
```


Przykładowy Dane:
```JSON
{
  "id": "21228c32-f966-480f-9c1c-af3faf4aaf83",
  "createdAt": "2023-06-06T00:00:00.000Z",
  "title": "Konsultacje z rodzicami:",
  "content": "06.06.2023r (wtorek) w godz. 18.00-19.00 odbędą się konsultacje dla rodziców. Dyrekcja szkoły",
  "published": true,
  "views": 27,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
  "publishedById": "82c50b88-97fb-46c3-8e85-222d83192b19"
}
```
### `posts/topPosts/` - zwraca najpopularniejsze posty sprzed 30 dni
> Możliwe zapytania - GET

> Api zwraca najpopularniejsze posty sprzed 30 dni. 
> Aby zapobiec sytuacji, w której fetch'ujemy więcej postów niż zostało opublikowane przez ostatnie 30 dni, funkcja zostałą podzielone na 2 części:
>1. Fetch'uje najpopularniejsze posty (wyznaczoną ilość)
>2. Jeżeli takich postów jest za mało, druga część funkcji, zwraca ostatnio opublikowane posty (tyle ile brakuje i takie, które nie zostały zwrócone w punkcie 1.)
>
>(Funckja defaulowo zwraca jeden, najpopularniejszy post.)

Argumenty (opcjonalne):
| Argument        | Wartości   |        
| ------------- |:-------------:| 
| count      |CYFRA | 


Przykładowy request:
```
api/posts/topPosts?count=2
```

Przykładowy Dane:
```JSON
[{
  "id": "21228c32-f966-480f-9c1c-af3faf4aaf83",
  "createdAt": "2023-06-06T00:00:00.000Z",
  "title": "Konsultacje z rodzicami:",
  "content": "06.06.2023r (wtorek) w godz. 18.00-19.00 odbędą się konsultacje dla rodziców. Dyrekcja szkoły",
  "published": true,
  "views": 26,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
  "publishedById": "82c50b88-97fb-46c3-8e85-222d83192b19"
},
{
  "id": "c7193fec-4a52-48bc-bfce-3144ab28f784",
  "createdAt": "2023-05-24T00:00:00.000Z",
  "title": "Systematycznie aktualizowane statystyki rekrutacji",
  "content": " \nRekrutacja 2023 na Tik Toku\n",
  "published": true,
  "views": 8,
  "titleImage": "/Archiwum.png",
  "gallery": [],
  "authorId": "28105da3-ece4-43e3-90a8-ba7b1e52de82",
  "publishedById": "28105da3-ece4-43e3-90a8-ba7b1e52de82"
}]
```