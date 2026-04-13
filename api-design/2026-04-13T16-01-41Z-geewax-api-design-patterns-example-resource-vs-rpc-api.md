# API Design Patterns | Example RPC vs. Resource Oriented 

Actions ("methods") for a flight-booking API (rpc based)

Method                  | Description
--                      | --
ScheduleFlight()        | Schedules a new flight
GetFlightDetails()      | Shows information about a specific flight
ShowAllBookings()       | Shows all travel plans currently booked
CancelReservation()     | Cancels an existing flight reservation
RescheduleFlight()      | Reschedules an existing flight to another date or time
UpgradeTrip()           | Upgrades from an economy class to first class

Pros:
- explicit, clearly defined

Cons:
- user must memorize each of the API methods (all subtly different)
- no stadardized way of interacting with the resources
- resources named different despite referring to same resource (i.e. `Flight`, `Reservation`)

Resource Orientation: aims to help standarized API design
- rely on "resources" being stored or interacted with
- small standard set of "actions" per resource (List, Get, Create, Update, etc)

Resource Oriented APIs are a specialized form of RPC-style APIs that follow
a standard, well-defined, clear pattern.

Shell for Resource-Oriented API actions (per resource)
Method                  | Description
--                      | --
CreateResource()        | Create a new <Resource>
GetResource()           | Show info about a specific <Resource>
ListResource()          | Show list of all existing <Resource>
DeleteResource()        | Delete an existing <Resource>
UpdateResource()        | Update an existing <Resrouce>

Modified version of the flight-booking API using **resource orientation**
> The underlying resoruce name is `FlightReservation`

Method                      | Description
--                          | --
CreateFlightReservation()   | Schedules a new flight reservation
GetFlightReservation()      | Show information about a specific flight reservation
ListFlightReservation()     | Show information about all flight reservations
DeleteFlightReservation()   | Delete a specific flight reservation
UpdateFlightReservation()   | Update a specific flight reservation

Resource-oriented APIs are not **strictly better** than RPC-oriented APIs. RPC-oriented
APIs shine withn API methods are stateless (i.e. `TranslateText()`, `EncryptAudio()`, etc.).
Resource-oriented APIs are typically easier to learn due to standardization of actions
on resources. Learning the API becomes just being aware of another resource, usually.
