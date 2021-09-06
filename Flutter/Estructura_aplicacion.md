Estructura_aplicacion.md

import 'package:flutter/material.dart';
import 'package:google_mobile_ads/google_mobile_ads.dart';
import 'ad_state.dart';
import 'package:provider/provider.dart';
import 'poema.dart';
import 'model.dart';

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

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  BannerAd banner;
  Poemario poemario = Poemario();
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    final adState = Provider.of<AdState>(context);

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