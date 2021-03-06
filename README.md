# Fio Bank Java Client

A Java SDK for accessing the [REST API](http://www.fio.cz/bank-services/internetbanking-api) of [Fio Bank](https://www.fio.cz/).

## Usage

The *Fio Bank Java Client* is available in [JitPack](https://jitpack.io/) Maven repository, to use it from Maven add to `pom.xml`:

```xml
<repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
</repository>
```

```xml
<dependency>
    <groupId>com.github.kapoun</groupId>
    <artifactId>fio-java</artifactId>
    <version>fio-java-0.2.0</version>
</dependency>
```

### Construct the FioClient
```java
FioClient fio = new FioClient("yourtoken");
```

### Get account statement

Get account statement with **the given number within the given year**:
```java
FioAccountStatement statement = fio.getStatement(2016, 1);
```

Get account statement within **the given period**:
```java
FioAccountStatement statement = fio.getStatement(LocalDate.of(2016, 1, 1), LocalDate.of(2016, 1, 31));
```

Get account statement from the **last download**:
```java
FioAccountStatement statement = fio.getStatement();
```

### Export account statement

Export account statement with **the given number within the given year**:
```java
fio.getStatement(2016, 1, ExportFormat.pdf, outputStream);
```

Export account statement within **the given period**:
```java
fio.getStatement(LocalDate.of(2016, 1, 1), LocalDate.of(2016, 1, 31), ExportFormat.pdf, outputStream);
```

Export account statement from the **last download**:
```java
fio.getStatement(ExportFormat.pdf, outputStream);
```

### Set last downloaded statement

Set last downloaded statement **by date**:
```java
fio.setLast(LocalDate.of(2016, 1, 1));
```

Set last downloaded statement **by transaction id**:
```java
fio.setLast("1147608198");
```

## Documentation

* [original documentation](http://www.fio.cz/docs/cz/API_Bankovnictvi.pdf)
* [local copy](API_Bankovnictvi.pdf)

## XML Schemas

* [IBSchema.xsd](http://www.fio.cz/xsd/IBSchema.xsd)
* [importIB.xsd](http://www.fio.cz/schema/importIB.xsd)
* [responseImportIB.xsd](http://www.fio.cz/schema/responseImportIB.xsd)
* [type.xsd](http://www.fio.cz/schema/type.xsd)
* [local copies](src/main/resources)


## License
The *Fio Bank Java Client* is free and open-source software under [BSD License](LICENSE.txt).

