# Sqlite database

There are two cases:
- create a new database
- use a preexisting database

## Process

### Add dependencies

```yaml
dependencies:
  flutter:
    sdk: flutter
  sqflite:
  path:
```
sqflite:https://pub.dev/packages/sqflite
path:https://pub.dev/packages/path

### Create the data model

```dart
class Dog {
  final int id;
  final String name;
  final int age;

  Dog({this.id, this.name, this.age});
}

// Convert a Dog into a Map. The keys must correspond to the names of the
  // columns in the database.
  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'name': name,
      'age': age,
    };
  }
```

### Add the Database Service class
If the database is preexisting, we need to load it from the assets before opening.

If the database is not preexisting, we don't need to open it but the tables in the schema have to be generated.


```dart
import 'dart:async';
import 'package:path/path.dart';
import 'package:sqflite/sqflite.dart';
import 'dog.dart';
import 'dart:io'; //para importar fichero
import 'dart:typed_data'; //para importar fichero
import 'package:flutter/services.dart'; //para importar fichero

class DatabaseService {
  static const String dbName = 'demo.db';
  Future<Database> database;
  String dbPath;
  String assetReference = 'assets/demo.db';
  bool isPreexisting = true;
  String sqlQuery;
  static const String newTable =
      'CREATE TABLE dogs(id INTEGER PRIMARY KEY, name TEXT, age INTEGER)';

  DatabaseService() {
    if (isPreexisting) {
      sqlQuery = '';
      loadDB();
      openDB(sqlQuery);
    } else {
      sqlQuery = newTable;
      openDB(sqlQuery);
    }
  }

  loadDB() async {
    String dbPath = join(await getDatabasesPath(), dbName);
    ByteData data = await rootBundle.load(assetReference);
    List<int> bytes =
        data.buffer.asUint8List(data.offsetInBytes, data.lengthInBytes);
    await File(dbPath).writeAsBytes(bytes);
  }

  openDB(String query) async {
    database = openDatabase(
      dbName,
      onCreate: (db, version) {
        '$query';
      },
      version: 1,
    );
  }

  Future<void> insertDog(Dog dog) async {
    final Database db = await database;
    db.insert(
      'dogs',
      dog.toMap(),
      conflictAlgorithm: ConflictAlgorithm.replace,
    );
  }

  Future<List<Dog>> dogs() async {
    // Get a reference to the database.
    final Database db = await database;
    final List<Map<String, dynamic>> maps = await db.query('dogs');
    return List.generate(maps.length, (i) {
      return Dog(
        id: maps[i]['id'],
        name: maps[i]['name'],
        age: maps[i]['age'],
      );
    });
  }
}
```
### Client calls
- Se crea una instancia del servicio de base de datos.
- Se inserta un elemento en la base de datos.
- Se lee la lista

```dart
WidgetsFlutterBinding.ensureInitialized();

  final dbs = DatabaseService();

  final fido = Dog(
    id: 0,
    name: 'Fidoddds',
    age: 5,
  );

  final toby = Dog(
    id: 2,
    name: 'Tobino',
    age: 3,
  );

  await dbs.insertItem(fido);
  await dbs.insertItem(toby);

  final lista = await dbs.items();
  print(lista[1].name);
  print(lista[0].name);
  print(lista[1].age);
}
```


## Preexisting database

### Add the Database Service class (new database)

```dart
class DatabaseService {
  static const dbname = 'demo.db';
  String dbPath;

  DatabaseService() {
    setDBpath();
    loadDB();
  }

  setDBpath() async {
    return dbPath = join(await getDatabasesPath(), dbname);
  }

  loadDB() async {
    ByteData data = await rootBundle.load("assets/demo.db");
    List<int> bytes =
        data.buffer.asUint8List(data.offsetInBytes, data.lengthInBytes);
    await File(dbPath).writeAsBytes(bytes);
  }

  final Future<Database> database = openDatabase(
    'demo.db', //setDBpath(), //dbname,
    onCreate: (db, version) {},
    version: 1,
  );

  Future<void> insertDog(Dog dog) async {
    final Database db = await database;
    db.insert(
      'dogs',
      dog.toMap(),
      conflictAlgorithm: ConflictAlgorithm.replace,
    );
  }

  Future<List<Dog>> dogs() async {
    final Database db = await database;
    final List<Map<String, dynamic>> maps = await db.query('dogs');
    return List.generate(maps.length, (i) {
      return Dog(
        id: maps[i]['id'],
        name: maps[i]['name'],
        age: maps[i]['age'],
      );
    });
  }
}
```

## References

Documentación oficial
https://esflutter.dev/docs/cookbook/persistence/sqlite

Implementación
https://www.youtube.com/watch?v=xrCBVwYjcvQ

Video de implementación
https://www.youtube.com/watch?v=xrCBVwYjcvQ&t=1669s