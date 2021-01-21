# Kafka Template Samples

Simple functions for Kafka Trigger and output bindings. 

# How to run it 

## Start the kafka broker 

I assume you already have a docker environmnet. 
Clone the Kafka extensions repo. It includes docker-composed

```bash
git clone git@github.com:Azure/azure-functions-kafka-extension.git
cd azure-functions-kafka-extension
docker-compose -f .\test\Microsoft.Azure.WebJobs.Extensions.Kafka.EndToEndTests\kafka-singlenode-compose.yaml up -d
```

## Install extension

This step and `extension.csproj` file will be removed once the extension bundle has been released. host.json is also modified.

```bash
func extensions install
```

## Run function

NOTE: TypeScript requires additional instruction. refer to [How to run the TypeScript](TypeScript/Readme.md)

```bash
func start
```

## Send message 

Send message to the http trigger with Kafka Output bindings. It will send message to the kafka broker and kafka trigger will be trigged.

Send message to `http://localhost:7071/api/KafkaOutput?message=hello`

## Clean up

```bash
 docker-compose -f .\test\Microsoft.Azure.WebJobs.Extensions.Kafka.EndToEndTests\kafka-singlenode-compose.yaml down
```