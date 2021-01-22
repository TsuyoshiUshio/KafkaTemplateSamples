# How to run the Java

For `func start`, replace the process by following.
Java use maven. You also don't need to do `func extensions install`.

```bash
mvn clean package
mvn azure-functions:run
```
