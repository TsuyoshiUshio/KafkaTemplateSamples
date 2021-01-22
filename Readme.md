# Kafka Template Samples

Simple functions for Kafka Trigger and output bindings. 

# How to run it 

## Start the kafka broker 

These template created for Kafak API of EventHubs. You can customise settings according to your broker types.
For creating Event Hub by following this [Quickstart: Create an event hub using Azure portal](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create). EventHub name should be `topic` for these examples.

## Configure `local.settings.json`

Copy `local.settings.json.example` to `local.settings.json` and update `{YOUR_EVENT_HUBS_NAMESPACE}` and `{YOUR_EVENT_HUBS_CONNECTION_STRING}`

```json
{
    "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "dotnet",
    "BrokerList": "{YOUR_EVENT_HUBS_NAMESPACE}.servicebus.windows.net:9093",
    "Password": "{YOUR_EVENT_HUBS_CONNECTION_STRING}"
  }
}
```

How EventHubs configured as a Kafka Broker.

| Kafka extension config | Description | EventHubs |
|------------- | --------------| ---------|
| BrokerList | The URL of the brokers | {YOUR_EVENT_HUBS_NAMESPACE}.servicebus.windows.net:9093 |
| Username | Username that is used for Kafka broker authentication | $ConnectionString (fix value) |
| Password | Password that is used for Kafka broker authentication | Event Hubs Connection String |
| Topic | Kafka Topic | EventHub refer to the [doc](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create#create-an-event-hub) |

## Install extension

This step and `extension.csproj` file will be removed once the extension bundle has been released. host.json is also modified.
**NOTE:** Java don't need this step.

```bash
func extensions install
```

## Run function

**NOTE:** TypeScript requires additional instruction. refer to [How to run the TypeScript](TypeScript/Readme.md)
**NOTE:** Java requires different instruction. refer to [How to run the TypeScript](Java/Readme.md)

```bash
func start
```

## Send message 

Send message to the http trigger with Kafka Output bindings. It will send message to the kafka broker and kafka trigger will be trigged.

Send message to `http://localhost:7071/api/KafkaOutput?message=hello`

## Clean up

Remove the EventHubs namespace's Resource Group.

