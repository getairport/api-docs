## POST /api/transfer

Create a transfer. Data should be sent as a JSON encoded string in POST body.

### Params:

```ts
type Request = {
    /**
     * Place.id transfer from
     */
    routeFrom: number;
    /**
     * Place.id transfer to
     */
    routeTo: number;
    /**
     * Date/Time of transfer in RFC 3339 format
     * @example 2025-03-30T02:03:04+02:00
     */
    dateTimeAt: string;
    /**
     * CarClass.id
     */
    carClass: number;
    /**
     * Client name for a greeting sign
     */
    greeting: string;
    /**
     * Client phones list
     */
    phones: Array<string>;
    /**
     * Client email
     */
    email: string;
    /**
     * Agent's Booking ID
     */
    bookingId: string | null;
    /**
     * Client Flight's ID
     */
    flightId: string | null;
    /**
     * Comment for Transfer Supplier
     */
    commentSupplier: string | null;
    /**
     * Comment for Transfer Driver
     */
    commentDriver: string | null;
    /**
     * Comment for Transfer Passenger
     */
    commentPassenger: string | null;
    /**
     * Passengers count
     */
    passengersCount: number | null;
}
```

### Response:

If the validation fails, the API returns 422 error.

Else, it returns following JSON results:

```ts
type Result = {
    /**
     * Internal transfer ID
     * @internal
     */
    id: number;
    /**
     * Bookind ID from request, or Server's internal generated Booking ID
     */
    bookingId: string;
};

type Response = Array<Result>;

const example: Response = {
    "id": 14,
    "bookingId": "GAS-14"
}
```
