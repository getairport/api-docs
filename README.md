# API docs

## Definitions
- `Server`: an API server that provides data and processes request (that is we)
- `Client`: a client, that requests `Server` to get data or to submit data (that is you)
- `User`: a user of Client's website/app that provides interface for communication with Server (that's your clients)
- `Route`: a combination of `Place from`, `Place to` and `Car Class` params
- `Transfer`: a submitted transfer creation request for the given Route to Server

## API description
- API is available at https://getairport.taxi remote.
- Client-Server communication is done using HTTP requests
- Requests and responses are in JSON format (request headers `Content-Type: application/json; Accept: application/json` should be set)

### Authorization
Client must add a header `Authorization: Bearer xxx-xxx-xxx` with every request.
The `xxx-xxx-xxx` part is an example token value, you'll be given a real token for API access.

Requests made with a wrong token, a token from disabled account, or without specifying it at all, will return 401 status response.

In case of 401 response, further details might be present in `www-authenticate` Server response header (it's optional).

## Client-Server communication algorithm

### 1. Get initial data
To get initial set of data to provide it to Users, Client has to get data from Server.

1.1. Client request [Cities](cities.md)<br>
1.2. Client request [Places](places.md)<br>
1.3. Client request [Car Classes](car-classes.md)

### 2. Provide interface for a User
When User interacts with Client's website/app the Client might request [Calculation](calculate.md) API
to provide information for the selected route such as price (and potentially other details, that might be added in future)

### 3. Create a Transfer
When User confirms creation of Transfer for the given price, Client should request [Create Transfer](create-transfer.md) API
