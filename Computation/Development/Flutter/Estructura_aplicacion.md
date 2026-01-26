# Application structure

## Import
Every file imports the packages that it needs.
```
import 'package:flutter/material.dart';
import 'package:google_mobile_ads/google_mobile_ads.dart';
import 'ad_state.dart';
import 'package:provider/provider.dart';
import 'poema.dart';
import 'model.dart';
```

## Top widget
- There is a widget that is at the top of the hierarchy. 
- If the class is stateful, the state returns a MaterialApp widget.
- the home parameter of the MaterialApp widget is the home page.
```
class MyApp extends StatefulWidget {
  // This widget is the root of your application.
  MyAppState createState() => MyAppState();
}

class MyAppState extends State<MyApp> {
  Poemario poemario = Poemario();
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Love Poems in Spanish',
      theme: ThemeData(
        primarySwatch: Colors.deepPurple,
      ),
      home: MyHomePage(title: 'Love Poems in Spanish'),
    );
  }
}
```

## Visuals
- The app has one or several pages to navigate
- Pages receive input from users
- Pages query the model to update its state

```
class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  BannerAd banner;
  Poemario poemario = Poemario(); //query to the model
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    final adState = Provider.of<AdState>(context); //auxiliary services
```
The declarative pattern specifies all the visible objects and embeds the actions in the widget structure.
```
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Column(
        children: [
          Expanded(
            child: ListView.builder(
              itemCount: poemario.ficheros.length,
              itemBuilder: (BuildContext context, int index) {
                return new Container(
                  padding: const EdgeInsets.all(8),
                  height: 50,
                  color: Colors.white,
                  child: ElevatedButton.icon(
                    style: ElevatedButton.styleFrom(
                      onPrimary: Colors.black54,
                      primary: Colors.amber[100],
                      textStyle: TextStyle(fontSize: 15),
                    ),
                    label: Text(poemario.nombres[index]),
                    icon: Icon(
                      Icons.eco,
                      color: Colors.green,
                    ),
                    onPressed: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                          builder: (context) => Poema(
                              title: 'assets/' + poemario.ficheros[index]),
                        ),
                      );
                    },
                  ),
                );
              },
            ),
          ),
          if (banner == null)
            SizedBox(height: 50)
          else
            Container(height: 50, child: AdWidget(ad: banner)),
        ],
      ),
    );
  }
}
```
## Model
- The model can have state (can be updated by the users actions) or can be stateless.
- If it is stateful, it is always updated by the View.
- The model can't change the View.
```
class Poemario {
  List<String> ficheros = [
    'PoemaAntesQueTu.md',
    'PoemaAQueMeLoDecis.md',
    'PoemaAsomabaASusOjos.md',
    'PoemaComoEnUnLibro.md',
    'PoemaComoSeArranca.md'
    ]
   }
 ```


## Auxiliary services
There are other services that provide auxiliary content like adds.

    adState.initialization.then(
      (status) {
        setState(
          () {
            banner = BannerAd(
              adUnitId: adState.bannerAdUnitId,
              size: AdSize.banner,
              request: AdRequest(),
              listener: adState.adListener,
            )..load();
          },
        );
      },
    );
  }
´´´
