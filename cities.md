## GET /api/cities

Return cities list

### Response:
```ts
type City = {
    id: number;
    name: string;
    timezone: string | null;
};

type Response = Array<City>

const example: Response = [
    {
        id: 1,
        name: "Ulaanbaatar",
        timezone: "Asia/Bangkok"
    }
]
```
