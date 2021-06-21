## Лицензия

Этот проект лицензируется в соответствии с лицензией Apache 2.0; подробности в файле LICENSE

## Авторы

 * Изначально написано Сергеем Козыревым [@taksebe](https://t.me/taksebe)
 * Readme edited by hypn

## Requirements

 * JSE JDK 11.0.5
 * [JUnit 5](https://junit.org/junit5/)

## Documentation

 * [core.telegram.org/bots](https://core.telegram.org/bots) - Telegram official API docs

## Miscellany

 * [Apache POI](https://poi.apache.org/) - создание документа Word
 * [Lombok](https://projectlombok.org/) - упрощение кода, замена стандартных java-методов аннотациями

## Сборка и запуск

```
git clone https://github.com/taksebe-official/mentalCalculation
cd mentalCalculation
mvn clean install
```

### Windows

```
set BOT_NAME=<имя бота>
set BOT_TOKEN=<токен бота>
java -Xmx300m -Xss512k -XX:CICompilerCount=2 -Dfile.encoding=UTF-8 -cp ./target/classes;./target/dependency/* ru.taksebe.telegram.mentalCalculation.MentalCalculationApplication
```

### Linux
```
export BOT_NAME=<имя бота>
export BOT_TOKEN=<токен бота>
java -Xmx300m -Xss512k -XX:CICompilerCount=2 -Dfile.encoding=UTF-8 -cp ./target/classes:./target/dependency/* ru.taksebe.telegram.mentalCalculation.MentalCalculationApplication
```

## Heroku deployment

 * Procfile, в котором устанавливается тип процесса (worker, web  и т.п.) и команда для запуска приложения
 * system.properties, в котором нужно указать версию Java, если она отлична от 8

```
mvn clean install
heroku login
heroku create <имя приложения>
git push heroku master
heroku config:set BOT_NAME=<имя бота>
heroku config:set BOT_TOKEN=<токен бота>
heroku config:get BOT_NAME
heroku config:get BOT_TOKEN
# установить количество контейнеров (dynos) для типа процесса worker (тип устанавливается в Procfile)
heroku ps:scale worker=1
heroku logs
```

В интерфейсе управления приложением на [heroku](https://www.heroku.com/) можно перейти к логам (прячутся под кнопкой «More» в правом верхнем углу) и убедиться, что приложение запущено.

## Отдельное спасибо от taksebe

 * [Владу](https://github.com/itotx), который возится со мной, неразумным
