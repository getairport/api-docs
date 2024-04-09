## GET /api/car-classes

Return car classes list

### Response:
```ts
type CarClass = {
    id: number;
    name: string;
    exampleCars: string | null;
    passengers: string | null;
    luggages: string | null;
    priority: number | null;
};

type Response = Array<CarClass>

const example: Response = [
    {
        "id": 2,
        "name": "Business",
        "exampleCars": "Subaru Impreza WRX STI Spec C Type RA-R",
        "passengers": "1",
        "luggages": "0",
        "priority": 1
    },
]
```
