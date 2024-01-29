# HelloID-Task-SA-Source-AzureActiveDirectory-AccountGetDetails

## Prerequisites
- [ ] This script uses the Microsoft Graph API and requires an App Registration with App permissions:
  - [ ] Read all users' full profiles <b><i>User.Read.All</i></b>

## Description

This code snippet executes the following tasks:

1. Define `$givenName` based on the `givenName` data source input `$dataSource.givenName`
2. Define `$middleName` based on the `middleName` data source input `$dataSource.middleName`
3. Define `$lastName` based on the `lastName` data source input `$dataSource.lastName`
4. Define `$UPNsuffix` based on the `employeeType` data source input `$dataSource.employeeType.UPNsuffix`
5. Creates a token to connect to the Graph API.
6. Generate `surname`.
7. Generate `displayname`.
8. Generate `userPrincipalName` and check if this is unique in Azure AD (using the API call: [Get a user](https://learn.microsoft.com/en-us/graph/api/user-get?view=graph-rest-1.0&tabs=http)), otherwise continue with next iteration.
9. Set `mail` equal to `userPrincipalName`.
10. Return a hash table for each user account using the `Write-Output` cmdlet.

> To view an example of the data source output, please refer to the JSON code pasted below and select the `Interpreted as JSON` option in HelloID

```json
{
    "givenName": "Janine",
    "middleName": "van den",
    "lastName": "Boele",
    "employeeType": {
        "Name": "Employee",
        "UPNsuffix": "devbreekie18.onmicrosoft.com",
        "Type": "Member",
        "Organization": "T4EJB"
    }
}
```