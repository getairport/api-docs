## GET /api/calculate/v2/:fromPlace/:toPlace

Get sale price for a route (v2).

### Params:

```ts
type Request = {
    /**
     * Place.id transfer from
     */
    fromPlace: number;
    /**
     * Place.id transfer to
     */
    toPlace: number;
}
```

### Response:

If the requested `fromPlace`, `toPlace` is not found the API returns 404 response.

Else, it returns following JSON results:

```ts
type CalculationResult = {
    /**
     * @internal Route id
     */
    id: number;
    /**
     * CarClass.id
     */
    carClass: number;
    /**
     * Sale price, in cents
     * @example 125 (means 1.25)
     */
    salePrice: number;
    /**
     * ISO 4217 Currency Code
     * @example USD
     */
    salePriceCurrency: string;
    /**
     * How many hours before a transfer date it can be created
     */
    minimalBookingHours: number | null;
};

type Response = Array<CalculationResult>;

const example: Response = [
    {
        "id": 1,
        "carClass": 1,
        "salePrice": 3000,
        "salePriceCurrency": "EUR",
        "minimalBookingHours": 24
    },
    {
        "id": 2,
        "carClass": 2,
        "salePrice": 5000,
        "salePriceCurrency": "USD",
        minimalBookingHours: null
    }
]
```
