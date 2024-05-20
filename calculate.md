## GET /api/calculate/:fromPlace/:toPlace/:carClass

> Deprecated. Please use new [Calculation v2](calculate-v2.md) API

Get sale price for a route.

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
    /**
     * CarClass.id requested car class
     */
    carClass: number;
}
```

### Response:

If the requested `fromPlace`, `toPlace` or `carClass` is not found the API returns 404 response.

Else, it returns following JSON results:

```ts
type CalculationResultSuccess = {
    success: true;
    /**
     * @internal Route id
     */
    id: number;
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

/**
 * Returned when route with requested params is not found or is not currently available
 */
type CalculationResultFailure = {
    success: false;
};

type Response = CalculationResultSuccess | CalculationResultFailure;

const exampleSuccess: Response = {
    "success": true,
    "id": 1,
    "salePrice": 3000,
    "salePriceCurrency": "EUR",
    "minimalBookingHours": 24
}
const exampleFailure: Response = {
    success: false
}
```
