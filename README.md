Assignment 2

Jag började med att byta namn på appen till "WilmerAppen":
```
<string name="app_name">WilmerAppen</string>
```

Jag fixade internet tillgång till appen med hjälp av koden:

```
<uses-permission android:name="android.permission.INTERNET" />
```

Sedan skulle det skapas ett WebView element i layout-filen content_main.xml genom att byta ut den befintliga TextView till WebView.
Efter det så sattes ett id på elementet.
Detta gjordes med följande kod:

```
<WebView
        android:id="@+id/my_webview"
```

En private member variable av typen WebView och med namnet myWebView skulle skapas och instansieras i funktionen onCreate().
Sedan skulle den tidigare Webview elementet som skapats i filen content_main.xml lokeras med hjälp av findViewById(R.id.my_webview).findViewById
Detta gjordes med hjälp av följande kod:

```
public class MainActivity extends AppCompatActivity {
    //Create private member variable
    WebView myWebView;
    ...

    protected void onCreate(Bundle savedInstanceState) {
            // Instantiate WebView
            myWebView = findViewById(R.id.my_webview);
            ...
```

Javascript skulle aktiveras i WebViewClienten. Och detta gjordes med två kodsnuttar bl.a getSetting() och setJavaScriptEnabled(true)
Koden ser ut som nedan:
```
// Enable Javascript to our WebViewClient
myWebView.getSettings().setJavaScriptEnabled(true);
```

En html sida skulle skapas och detta gjordes genom att högerklicka på app-mappen -> new -> folder -> assets folder och sedan namngavs den about.html.

Nästa uppgift var att implementera showExternalWebPage och showInternalWebPage med loadUrl(), myWebView.loadUrl(...) lades in för respektive showInternal och showExternalWebPage.
Sedan skulle dessa kallas på inom funktionen onOptionsItemSelected(MenuItem item). Detta gjordes genom att lägga in funktionen showExternalWebPage i den första if-satsen där external web page skulle visas, och likadant för showInternalWebPage.
Detta gjordes för att i appens dropdown meny ska kunna komma till externalwebpage och internalwebpage.
Detta gjordes med hjälp av följande kod:

```
public class MainActivity extends AppCompatActivity {

    public void showExternalWebPage(){
        myWebView.loadUrl("https://wwwlab.iit.his.se/b21willu/App-prototyp/app-prototyp.html");
        // TODO: Add your code for showing external web page here
    }

    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/about.html");
        // TODO: Add your code for showing internal web page here
    }


        public boolean onOptionsItemSelected(MenuItem item) {
            int id = item.getItemId();

            //noinspection SimplifiableIfStatement
            if (id == R.id.action_external_web) {
                showExternalWebPage();
                Log.d("==>","Will display external web page");
                return true;
            }

            if (id == R.id.action_internal_web) {
                showInternalWebPage();
                Log.d("==>","Will display internal web page");
                return true;
            }
            ...
```




![](Screenshot.png)
Bild på dropdownmeny samt appens startsida.

Gick inte att ta en screenshot ifrån min external page. Misstänkter att det har o göra med att wwwlab.iit.his.se inte funkar längre.
