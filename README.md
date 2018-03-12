
# Hackathon 20h - JavaScript - Budgety

El objetivo del hackathon consiste en modificar la aplicación Budgety de la siguiente manera:

1- Adaptar la aplicación a una estructura modular que mejore la legibilidad y el mantenimiento del código.

2- Incluir persistencia de los datos de manera local, para que la información siga presente después cerrar y volver a abrir la aplicación.

Para ello, comenzaremos clonando el repositorio con la estructura base:

*$ git clone **[https://github.com/20Heroes/budgety-app-base.gi*t](https://github.com/20Heroes/budget-app-base.git)

Instalaremos todas las dependencias necesarias:

*$ npm install*

Ejecutaremos el servidor web que servirá la aplicación y tendrá en cuenta todos los cambios que vayamos produciendo en el código:

*$ npm run watch*

La aplicación estará accesible en la dirección *[http://localhost:300*0](http://localhost:3000)

## Guía de referencia

### Estructura modular

Separar cada controlador en un archivo independiente, en una estructura similar a la que sigue

app.js

|-- components

|---- AppController.js

|---- BudgetController.js

|---- UIController.js

El módulo principal *AppController* importa al resto de módulos secundarios mediante el uso de *import*. 

Cada módulo secundario *BudgetController* y *UIController* exporta su funcionalidad mediante el uso de *export*.

No hay que hacer ningún cambio en la funcionalidad, tan sólo adaptar el código de cada controlador para que su funcionalidad pública sea exportable mediante un módulo. 

Ejemplo:

[https://gist.github.com/guimochila/07af2b30b0ca9ef55665c2b098969d7b](https://gist.github.com/guimochila/07af2b30b0ca9ef55665c2b098969d7b)

Partiendo del código base *module-pattern-es5.js*, se adapta a una estructura modular: *app.js*, *MainController.js*, *BooksController.js*.

Referencias: 

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

[https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export)

### Persistencia de los datos

Para mantener la información, haremos uso de la Web Storage API, concretamente de Local Storage.

A tener en cuenta:

* La nueva funcionalidad deberá estar encapsulada en un nuevo módulo aparte.

* Cada vez que se inicie la aplicación, se procederá a la carga de la información, en caso de que haya sido previamente almacenada.

* Local Storage tan solo permite almacenar cadenas de texto, por lo que será necesaria una conversión en los datos internos de la aplicación mediante el uso de JSON.stringify y JSON.parse.

* Cada vez que se añadan o eliminen entradas, se procederá a persistir de nuevo toda la información.

Referencias:

[https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)
