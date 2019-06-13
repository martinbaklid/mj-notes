# Logger API

> Programmeringsspråk: valgfritt

## Funksjoner

Lag et HTTP API med følgende funksjoner:
- Endepunkter for logging:  
  POST `localhost:8080/api/log` body: `{ text: "some log line", level: <LOGLEVEL>` : legg til logglinje  
  GET `localhost:8080/api/log` : hent 100 siste logglinjer  
  GET `localhost:8080/api/log?lines=X` : hent X siste logglinjer
- Når du legger til en logglinje, legg på timestamp
- Logg til fil, konsoll, JSON, og en annen valgfri logger
    * På fil-loggeren må det være funksjonalitet for å skrive til ny fil dersom en fil blir for lang.
      I denne oppgaven vil det si fem linjer. Du skal da få: `log-<DATO>-0.log`, `log-<DATO>-1.log`, osv.

Ta utgangspunkt i eksempelkoden under. Denne koden er på ingen måte optimalisert, så første del av oppgaven
kan være å optimalisere denne. Ta da utgangspunkt i SOLID-prinsippene for objektorientert programmering.

## Eksempelkode

`Application.java`
```java
package no.itera;

import no.itera.logger.LogEngine;

public class Application {
  public static void main(String[] args) {
    LogEngine logEngine = new LogEngine();

    logEngine.writeLogMessage("Hello");
    logEngine.writeLogMessage("World");
  }
}
```


`LogEngine.java`
```java
package no.itera.logger;

public class LogEngine {
  private static final FileLogger FILE_LOGGER = new FileLogger();
  private static final ConsoleLogger CONSOLE_LOGGER = new ConsoleLogger();
  private static final JsonLogger JSON_LOGGER = new JsonLogger();

  public void writeLogMessage(String message) {
    CONSOLE_LOGGER.writeToConsole(message + "\n");
    try {
      FILE_LOGGER.writeToFile(message + "\n");
    } catch (Exception e) {
      // NOP
    }
    JSON_LOGGER.writeToJsonLog(message);
  }
}
```


`JsonLogger.java`
```java
package no.itera.logger;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;
import java.util.Date;

public class JsonLogger {
  private static final String LOG_FILE_NAME = "log.json";

  public void writeToJsonLog(String message) {

    try {
      Path filePath = Paths.get(LOG_FILE_NAME);

      if (filePath.toFile().exists()) {
        Files.write(
            filePath,
            String.format("{ \"date\": \"%s\", \"message\": \"%s\" }\n", new Date().toString(), message).getBytes(),
            StandardOpenOption.APPEND
        );
      } else {
        Files.write(
            filePath,
            String.format("{ \"date\": \"%s\", \"message\": \"%s\" }\n", new Date().toString(), message).getBytes(),
            StandardOpenOption.CREATE
        );
      }
    } catch (IOException ioException) {
      System.out.println("Logging failed");
    }
  }
}
```


`FileLogger.java`
```java
package no.itera.logger;

import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;
import java.util.Date;

public class FileLogger {
  private static final String LOG_FILE_NAME = "log.txt";

  public void writeToFile(String message) throws Exception {

    Path filePath = Paths.get(LOG_FILE_NAME);

    if (filePath.toFile().exists()) {
      Files.write(
          filePath,
          String.format("%s %s", new Date().toString(), message).getBytes(),
          StandardOpenOption.APPEND
      );
    } else {
      Files.write(
          filePath,
          String.format("%s %s", new Date().toString(), message).getBytes(),
          StandardOpenOption.CREATE
      );
    }
  }
}
```


`ConsoleLogger.java`
```java
package no.itera.logger;

import java.util.Date;

public class ConsoleLogger {
  public void writeToConsole(String message) {
    System.out.format("%s %s", new Date().toString(), message);
  }
}
```
