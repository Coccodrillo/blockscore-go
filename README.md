# blockscore
Go client library for the BlockScore API.

Note:
* Some of the APIs may not be idiomatic Go, this is in order to keep those APIs as similar to existing BlockScore client libraries as possible.
* Some things will be grammatically incorrect (i.e., "get a People" rather than "get a Person"), this is in order to remain consistent with BlockScore API endpoint names, for which things make sense.

## Usage

Set your BlockScore API key in an environment variable:

```bash
export BLOCKSCORE_API_KEY="your key"
```

*Note: Make sure to use your test key when running the test suite, otherwise the test suite will make live API requests.*

### Client Creation

```go
client = blockscore.Client.new("YOUR_BLOCKSCORE_API_KEY")
```

### People

Create a new person:

```go
params := blockscore.PeopleParams{
    NameFirst:          "John",
    NameMiddle:         "P",
    NameLast:           "Denver",
    DocumentType:       "ssn",
    DocumentValue:      "0000",
    BirthDay:           7,
    BirthMonth:         6,
    BirthYear:          1980,
    AddressStreet1:     "1234 Main Street",
    AddressStreet2:     "APT 12",
    AddressCity:        "Palo Alto",
    AddressSubdivision: "California",
    AddressPostalCode:  "94025",
    AddressCountryCode: "US",
    PhoneNumber:        "123-456-78910",
    IPAddress:          "127.0.0.1",
    Note:               "Hello, world",
}

person, err := client.People.Create(&params)
```

Get a single existing People:

```go
person, err = client.People.Retrieve("DESIRED_PERSON_ID")
```

Get a list of People:

```go
people, err = client.People.List()
```

Get a list of X people, offset by Y people:

```go
people, err = client.People.ListN(X, Y)
```

### Companies

Create a new company:

```go
params := blockscore.CompanyParams{
    EntityName:               "BlockScore",
    TaxId:                    "123410000",
    IncorporationState:       "DE",
    IncorporationCountryCode: "US",
    IncorporationType:        "corporation",
    IncorporationDay:         23,
    IncorporationMonth:       8,
    IncorporationYear:        1993,
    Dbas:                     "BitRemit",
    RegistrationNumber:       "123123123",
    Email:                    "test@example.com",
    Url:                      "https://blockscore.com",
    PhoneNumber:              "6505555555",
    IPAddress:                "67.160.8.182",
    Note:                     "Much wow",
    AddressStreet1:           "12345 Main Street",
    AddressStreet2:           "#12",
    AddressCity:              "Palo Alto",
    AddressSubdivision:       "CA",
    AddressPostalCode:        "94025",
    AddressCountryCode:       "US",
}

company, err := client.Companies.Create(&params)
```

Get a single existing Company:

```go
company, err = client.Companies.Retrieve("DESIRED_COMPANY_ID")
```

Get a list of Companies:

```go
companies, err = client.Companies.List()
```

Get a list of X companies, offset by Y companies:

```go
companies, err = client.Companies.ListN(X, Y)
```
