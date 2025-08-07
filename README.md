# Camel Entra Sync Demo

This repository contains a demo project that illustrates how to use Apache Camel to fetch members of a Microsoft Entra ID group and export them to a CSV file. The project demonstrates authentication with Microsoft Entra ID, querying group members, and handling nested group memberships. This demo has been tested with Apache Camel version 4.10.

## Configuration

The project uses a configuration file named `application.properties` to manage settings such as authentication details and group names. Ensure you configure the following properties:

- `ms.login.uri`: The authentication endpoint for your Microsoft Entra ID.
- `token_grace_period`: The grace period in seconds before token expiration.
- `ad_group.display_name`: The display name of the group whose members you want to fetch.
- `ms.graph.tenant_id`: Your Microsoft Entra ID tenant ID.
- `ms.graph.client_id`: Your application's client ID.
- `ms.graph.client_secret`: Your application's client secret.

## Prerequisites

Before running this demo, you need to register an application in Microsoft Entra ID:

1. Go to the Microsoft Entra admin center.
2. Navigate to "App registrations" and click on "New registration".
3. Enter a name for your application and select the appropriate account types.
4. After registration, note down the `Application (client) ID` and the `Directory (tenant) ID`.
5. Under "Certificates & secrets", create a new client secret and note it down.
6. Ensure your application has the necessary permissions to read directory data.

## Running the Demo

To run the demo, use the following command:

```bash
camel run application.properties auth-handler.camel.yaml list-group-members.camel.yaml
```

This command starts the Camel application, which authenticates with Microsoft Entra ID, fetches the group members, and exports them to a CSV file named `group-members.csv` in the `groups` directory.

## Stopping the Application

The Camel application will continue to run after processing the routes. You can stop it at any time by pressing `Ctrl-C` in the terminal.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## About the Author

This project is developed by [Digital Change GmbH](https://digitalchange.eu). We specialize in system integration implementation by using Apache Camel.
