## GET /api/places[/:cityId]

Return places list

### Params:

```ts
type Request = {
    /**
     * City.id (optional) restrict places list to given City
     */
    cityId?: number;
}
```

### Response:
```ts
type Place = {
    id: number;
    cityId: number;
    name: string;
};

type Response = Array<Place>

const example: Response = [
    {
        "id": 1,
        "cityId": 1,
        "name": "Chinggis Khaan International Airport (IATA: UBN, ICAO: ZMCK)"
    }
]
```
