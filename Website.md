# API
> API serwera znajduje się w folderze: `./app/api/`

# Ścieżki:

## `auth/[...nextAuth]` - ścieka wykorzystywana przez NextAuth przy logowaniu, itd.</summary>


## `calendar/`


### `days/`
### `events/`
> Możliwe zapytania - GET

Argumenty:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| count      |CYFRA | 

Body zapytania:
| Argument        | Wartości           | 
| ------------- |:-------------:| 
| year      |ROK | 
| month      | od 0 do 11      | 
| day | od 0 do 27-30     |  


Przykładowy request:
```
 /api/calendar/events?count=3
```

### `getNumbers/` - zwraca wszystkie 'szcześliwe' numerki.
> Możliwe zapytania - GET

 Argumenty:
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
 [
  {
    "number": 24,
    "date": "20-10-2023"
  }
]
 ```

### `getWeekNumbers/` - zwraca 'szcześliwe' numerki z bieżącego tygodnia
Przykładowy Dane:
 ```JSON
[
  {
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
  }
]
```

Przykładowy request:
```
api/calendar/getWeekNumbers
```
