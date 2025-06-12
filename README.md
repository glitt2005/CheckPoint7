# Check Point 7 - ejercicios teóricos y prácticos.

## 1. ¿Qué diferencia a Javascript de cualquier otro lenguaje de programación?

1.  _JavaScript_ es el **único programa** que puede ser **interpretado por un navegador/buscador Web**. Cientos de lenguajes y entre ellos _Python, Java, Ruby, C,_ etc.: todos necesitan estar en un servidor, y si estamos construyendo una página web, ese servidor tiene que construir todos estos procesos y envolver ese código de una forma que el navegador/explorador lo entienda.    _JavaScript_ es un poco diferente: fue **creado** para ello, **para** que pudiera **ser interpretado por los navegadores**. Esto quiere decir que puedes escribir código _JavaScript_ y simplemente abrirlo en **el buscador**, éste lo **analiza, interpreta y ejecuta el programa**. Y eso nos lleva al punto 2:

    \

2.  Por ello, algunas de las **aplicaciones más potentes están escritas en** _JavaScript_. En el aprendizaje de un desarrollador, enseguida se encontrará con código de _JavaScript_ de una manera u otra. _**Gmail, Twitter, Facebook**_ usan _JavaScript_ extensamente. De hecho, **Google**, que es propietario de _Gmail_ y de _Facebook_, ha creado **su propio marco** de _JavaScript_ (sus propias capas encima de _JavaScript_) lo que hace posible que **los desarrolladores puedan crear su propias aplicaciones** utilizando _JavaScript_.

    \

3.  En la construcción de **aplicaciones móviles**, _JavaScript_ es el lenguaje adecuado hoy en día. Antes cada teléfono tenía su propio lenguaje de programación, pero _JavaScript_ **construyó con sus propias bibliotecas** y sus propias plataformas (_las plataformas o **frameworks** son plantillas o un conjunto de herramientas y componentes predefinidos que proporcionan una base para desarrollar aplicaciones o software_).    _JavaScript_ permite a los desarrolladores **crear software más rápidamente, de manera más eficiente y organizada**, utilizando componentes reutilizables y funcionalidades ya implementadas que permitirán construir aplicaciones utilizando solo _JavaScript_ que se **vincularán directamente a la API de tu smart phone**. Esto significa que podemos crear una aplicación que por ejemplo puede **acceder a la cámara, verificar la ubicación, usar el acelerómetro, etc**. Antes necesitabas utilizar otro lenguaje para esto.

    \

4. Es una de las herramientas más poderosas que se puede tener en el arsenal para automatizar el flujo diario de trabajo, muy útil incluso aunque no seas desarrollador. Por ejemplo:
   * **Tareas repetitivas, mecánicas** y pesadas que se tienen al **trabajar en una oficina**: muchas de ellas se podrían automatizar con _JavaScript_,
   * Al poderse ejecutar directamente en el navegador, si tenemos **una gran página web** a la que solamos frecuentar y necesitamos hacer **click en un botón cientos de veces** (_p.ej para actualizar y seguir a un grupo de personas en **Instagram o LinkedIn**)_. En _JavaScript_ sería fácil **crear un sencillo script** que al ejecutarse **automatice** esto en lugar de hacerlo manualmente.

_JavaScript_ es muy flexible, y esto a veces tiene sus implicaciones en cuanto al cuidado que debemos tener.

Vamos a ver algunos de los puntos particulares en cuanto al funcionamiento concreto de _JavaScript_:\


#### 1. EL ÁMBITO DE LAS VARIABLES (VARIABLE SCOPE). 

A) Variable GLOBAL

```javascript
var usuario = {
email: 'prueba@gmail.com',
nombre: 'David Casas'
}
function saludo(){
console.log("Hola, ".concat(usuario.nombre));
}

saludo();   // devuelve: "Hola, David Casas"
```

B) Variable LOCAL

```javascript
function saludo() {
  var usuario = {
    email: 'prueba@gmail.com',
    nombre: 'Federico Faggin'
  }
  console.log("Hola, ".concat(usuario.nombre));
}

saludo();  // "Hola, Federico Faggin"
```

El problema es que si imprimimos el valor de la variable:

```javascript
console.log(usuario.nombre)    // Devuelve: "David Casas"

```

podemos ver que NO ha cambiado la variable. `"Federico Faggin"` está a nivel **local** (su variable `usuario`) se encuentra a nivel **local**, y `console.log` está a nivel **global**, por tanto, llama a la variable `usuario`de más arriba, la **gobal**.

C) Otra cosa muy PARTICULAR Y CURIOSA de _JavaScript_ con la que **debemos tener mucho cuidado** es que (en este ultimo caso de VARIABLE LOCAL) si simplemente **eliminamos la expresión `var`** **ya no sería una variable**, sería un **objeto**, y _JavaScript_ ya **no interpretaría como variable local**, por lo que si hiciéramos un:

```javascript
console.log(usuario.nombre)    // Devolvería "Fedecirco Faggin"!!!

```

BUENAS PRÁCTICAS:\
Para **no contaminar la variable** deberíamos:

* **evitar tener variables globales**, o bien tener un número muy limitado de ellas. Siempre podremos utilizarlas (accediendo a ellas de la forma adecuada) sin correr riesgos innecesarios.
* Además, debemos no olvidarnos de poner **var** o **let** cuando declaramos las variables, si no, **accidentamente podríamos crear variables globales**

\


#### 2. HOISTING O ELEVACIÓN

Otra característica prácticamente particular de _JavaScript_ es el **hoisting** o elevación: Se refiere a la **forma** específica que _JavaScript_ **lee las variables**, y tiene que ver con **dónde se definen las variables, en qué orden**. Si se lo hacemos en el orden incorrecto, **habrá errores**.

**EJEMPLO:**

Si **asignamos** una variable de esta forma:

```javascript
nombre = "Sammy";
console.log(name);
```

Y luego **declaramos**:

```javascript
var name;    		//    Devuelve "Sammy"
```

Aquí no hay problema. ¿Qué hace _JavaScript_?

1. Examina todos los sitios en los que **haya declarado una variable** (`var name`)
2. Lo pre-carga **en la parte superior**. Es decir cuando escribimos `var name` , en realidad es como si lo subiera **arriba del todo**:

```javascript
var name;
name = "Sammy";
console.log(name);
```

por eso se llama **Hoisting**, porque en realidad es virtualmente **“subida” o elevación**.

**¡OJO!:**\
El **hoisting** solo funciona con DECLARACIONES, **no funciona con ASIGNACIONES** :

```javascript
Console.log(edad);
var edad = 19;     //  devuelve -- >  undefined
```

Aquí no solo hemos DECLARADO la variable, **también la hemos ASIGNADO (al mismo tiempo**). Esto lo ve diferente comparado que si SOLO la DEFINIMOS.

\


BUENAS PRÁCTICAS:\
Debemos evitar problemas de **hoisting**: **mejor declararlas al principio** para evitar este tipo de problema.

\
\


## 2. ¿Cuáles son algunos tipos de datos JS?

Una primera distinción es datos PRIMITIVOS y NO PRIMITIVOS.

En _JavaScript_, un **PRIMITIVO** o **primitive** (valor primitivo, tipo de dato primitivo) son datos que **no son un objeto y no tienen métodos** (por lo tanto, estos últimos serían **NO PRIMITIVOS**) Hay 6 tipos de datos primitivos: **string, number, bigint, boolean, undefined y symbol**.\
También hay **null**, que aparentemente es primitivo, pero de hecho es un caso especial, lo considera _**Object**_: y cualquier tipo estructurado se deriva de **null** por la Cadena de prototipos.

La mayoría de las veces, un valor primitivo se representa directamente en el nivel más bajo de la implementación del lenguaje.

Todos los primitivos son **inmutables**, es decir, no se pueden modificar. Es importante **no confundir un primitivo en sí mismo con un valor primitivo asignado a una variable**. **Se puede reasignar un nuevo valor a la variable, pero el valor existente no se puede cambiar** de la misma forma en que se pueden modificar los objetos, los arreglos y las funciones.

\


**1) ALGUNOS TIPOS DE DATOS**

\


1. Cadena de texto (**string**)   \
   El tipo de datos **string** representa una secuencia de **caracteres, como texto o palabras**. Las cadenas se deben encerrar entre **comillas simples ' ' o dobles " "**.

```javascript
var cat = 'Sammy';
let dog = "Mixie";
```

\


2. Números (**number**)

El tipo de datos **number** en _JavaScript_ representa **tanto números enteros como de punto flotante**.

```javascript
var edad = 25;
let precio = 99.95;
```

\


3. Booleano (**boolean**)

El tipo de datos **boolean** representa un valor de _VERDAD_, que puede ser `true` (verdadero) o `false` (falso). Es útil en expresiones condicionales y lógicas.

```javascript
var precioMarcado = true;
var clienteVIP = false;
```

\


4. Null o nulo (**null**)

En _JavaScript_, **null** es un valor especial que representa la **ausencia intencional** de cualquier objeto o valor. Está vacío, pero es el caso de cuando una variable ha sido declarada, y **se le ha asignado explícitamente el valor de `null`**. O sea, que como hemos dicho al principio, **no** es un dato **primitivo**. Por otra parte, _JavaScript_ interpreta `null`\*\* como de tipo **objeto** sin inicializar.

```javascript
var usuarioAdmin = null;
console.log(typeof usuarioAdmin);   //devuelve: "object"
```

\


5. Undefined (**undefined**)

El valor **undefined** (no definido) indica que una variable **ha sido declarada pero aún no se le ha asignado ningún valor**. Hay muchas veces que te crees que tienes acceso a algún valor, o **crees que fijaste el valor**, pero luego te das cuenta que devuelve **undefined**, lo que quiere decir que en algún punto en donde debería estar asignado el valor, pues **se te ha pasado, se ha saltado por error este paso**, y entonces deberá ser definida más tarde. Está muy bien **para saber si un valor se definió o no**, y se utiliza mucho para tareas de _depuración_ o **debugging**. No hay que confundirlo con `null`que como hemos dicho éste último se asignó intencionadamente.

```javascript
var casa;
console.log(casa); // Devuelve:  undefined
```

\


6. Símbolo (**symbol**)

El tipo de datos **symbol** es único y se utiliza para **identificadores únicos de objetos**. Podemos añadirle o no una **descripción, es opcional**, y podrá ser útil en la **depuración** del código.\
Como decimos, se garantiza que los **símbolos son únicos**. Aunque declaremos **varios Symbols con la misma descripción**, éstos tendrán **valores distintos**. La descripción es solamente una etiqueta que no afecta nada más.

```javascript
var miSimbolo = Symbol('iris');
```

\


7. Objetos (**object**)

Como hemos dicho, es un tipo de datos NO PRIMITIVO. Los **objetos** en _JavaScript_ son colecciones de **pares clave-valor**, donde la **clave** es una _**cadena (o símbolo)**_ y el **valor** puede ser _**cualquier tipo de dato**_, incluidos otros objetos. En cuanto a la **sintaxis**:\
\- Utilizaremos **llaves {}**,\
\- Si tenemos **un solo clave-valor**, lo podemos poner en **una línea**.\
\- Para **varios pares clave-valor**, con **comas en varias líneas**, como vemos en el siguiente ejemplo.\
\- Para **acceder al valor de una clave**, utilizaremos el **dot notation** o notación por puntos.

```javascript
var cliente1 = {
    nombre: 'Ana',
    edad: 30,
    coche: false
};
```

Accediendo al **valor de la clave** `nombre`:

```javascript
var cliente1 = {
    nombre: 'María',
    edad: 30,
    coche: false
};

console.log(cliente1.nombre);    //Devuelve:  "María"
```

Para **cambiar el valor** de una variable utilizamos **la misma sintaxis** de **dot notation** o notación por puntos:

```javascript
var casa = { campo: 150 };
casa.campo = 125;

console.log(casa.campo);        //Devuelve:  125
```

En el caso de **objectos anidados**, accederemos al valor también mediante **dot notation** así:

```javascript
var cliente1 = {
    nombre: 'Ana',
    edad: 30,
    coche: false,
    habilidades: {
      pintura: 8,
      escultura: 5,
      música: 7
    }
};

console.log(cliente1.habilidades.pintura);   //Devuelve  8
```

Por último, podemos **añadir objetos sobre la marcha**, de forma **dinámica**. Añadiendo un campo más dentro de `habilidades`:

```javascript
cliente1.habilidades.caligrafia = 9;

console.log(cliente1.habilidades.caligrafia);  //Devuelve 9
```

\


8. Arrays / arreglos (**array**)

De nuevo un tipo de dato NO PRIMITIVO. Los **arrays** en _JavaScript_ son **objetos** especiales que permiten almacenar **múltiples valores en una sola variable**, indexados numéricamente y son mutables. Cada vez que _JavaScript_ almacene una lista de elementos, normalmente será en un **array** o en una estructura de datos muy similar.\


**CASO DE APLICACIÓN DE LOS ARRAYS:**

* Si creamos **una web de un directorio** como _Páginas Amarillas_ o _Yelp_, y contactamos un **API**, ésta nos enviará una **lista o una colección de elementos**, y _JavaScript_ lo va a interpretar o lo va a poner dentro de un **array**.
* Así que, en el caso de llamar a una **base de datos**, o a una **API**, si queremos obtener cualquier tipo de **colección**, _JavaScript_ lo pondrá en un **array**. Por esto **los arrays** son tan frecuentes en _JavaScript_.

En _JavaScript_ podemos poner **en una variable** todo tipo de elementos: **números, strings, objetos, funciones...**¡Enseguida se pone la cosa bastante confusa!\
Pero si tenemos **los mismos tipos de datos**: por ej. una gran cantidad de **usuarios**, un listado de **restaurantes**, o publicaciones de **blogs**… generalmente los almacenas en un **array**. Nos es útil tener una estructura de datos donde almacenar un único array **dentro de una variable** y así poder trabajar con ella.

\


_**Dos formas principales para crear un array:**_

\


1. **A TRAVÉS DE LA PALABRA CLAVE `new` y el constructor `Array()`**

EJEMPLOS:

* _Un array con **3 elementos**_:

```javascript
var generandoArray = new Array(3);

generandoArray;      // Devuelve  [object Array] (3)
                     //           [,,]

```

* _Un array con **3 nombres**_:

```javascript
var generandoArray = new Array("rojo", "verde", "azul");

generandoArray;      // Devuelve  ["rojo","verde","azul"]             
```

\
\


2. **A TRAVÉS DE LA SINTAXIS LITERAL DEL ARRAY, con el uso de corchetes \[ ]**

EJEMPLOS:

a) _Un array de 3 elementos y **averiguando el nº de ellos**_:

```javascript
var miArray = ["Mixie", "Sammy", "Cloe"];

miArray.length;    // Devuelve  3
```

b) _Un array con elementos con **diferente tipo de dato** e incluso **anidados**_:

```javascript
var arrayMezclado = ['Mixie', 1, ['gris', 'rojo', 'negro'], { name: 'Sam' }, function casa() { console.log('venta');}]
```

c) **Obteniendo información de array**: utilizamos **corchetes con el índice dentro** \[índice]::

```javascript
var arrayMezclado = ['Mixie', 1, ['gris', 'rojo', 'negro'], { nombre: 'Sam' }, function casa() { console.log('venta');}]

console.log(arrayMezclado[2][0]);      // devuelve "gris"
console.log(arrayMezclado[3]);         // devolviendo el objeto: { nombre: 'Sam' }
console.log(arrayMezclado[3].nombre);  // devolviendo el valor de la clave del objeto: "Sam"
console.log(arrayMezclado[4]);         // devolviendo la función: function casa() {console.log('venta');}
console.log(arrayMezclado[4]());       // devolviendo la función ejecutada: "venta"  -undefined
```

En la última línea, vemos algo muy común: **retornar un método dentro de un objeto**.

\


Una de las maneras más fáciles de entender la forma que los **arrays** funcionan en _JavaScript_ es pensar en ellos como una **colección de todos los elementos** que hemos venido utilizando hasa ahora: no hay nada de especial en ello. Recogen todo tipo de cosas, puedes poner lo que sea dentro de un array. **Solo hay que tener en cuenta la forma de almacenar**.

\
\


**2) CONSULTA DEL TIPO DE DATOS: uso de `typeof`**

Debemos saber **qué tipos de datos** tenemos **para** aplicar las funciones correctas y **no incurrir en errores**. Para comprobarlo utilizamos la función `typeof`seguido de la variable o el valor que sea:

```javascript
typeof 45;                  //devuelve: "number" 
typeof "Semana";            //devuelve: "string"
typeof { precio1 : 450 };   //devuelve: "object"
typeof true;                //devuelve: "boolean"

var edad;
typeof edad;                //devuelve: "undefined"

edad = null;
typeof edad;               //devuelve:  "object"

```

\


_**CASO PRÁCTICO DE USO:**_\
Imaginemos **una aplicación web** y no sabemos **si todos los valores que retornan están completos**. Sabemos a lo que tenemos acceso PERO no qué elementos realmente contienen algo.

*   Por ejemplo, uno de los atributos de la aplicación web es un **usuario de&#x20;**_**Twitter**_**, pero OPCIONAL**, por lo que la información puede estar ahí o no:

    * **en el caso de que la información esté**, podríamos hacer clicable un **enlace** que lleve a la página de perfil de _Twitter_.
    * **en el caso de que NO exista esta info**, haríamos que el **enlace no se mostrara** para nada.

    Aquí, necesitaríamos confirmar si el valor es **`undefined`** o si, por el contrario, simplemente no está relleno al ser opcional; sería el caso de `null`.

\
\


**3) CAMBIO DEL TIPO DE DATOS o DATA CASTING**

\


_JavaScript_ intenta hacerlo de forma **automática**. A veces no resulta tan buena idea porque se pueden producir **equivocaciones**:

1. En una SUMA si al menos **uno de los dos sumandos** es _**string**_ entonces lo va a convertir todo en _**string**_:

```javascript
"30" + 20;          //devuelve: "3020" 
```

2. En una RESTA o con `null`interpreta como números:

```javascript
"30" - 20;          //devuelve: 10
25 + null;          //devuelve: 25 
```

**`null` lo convierte a 0** porque asume que se trata de algún cálculo y que no queremos tomar nulo como un valor. Interpreta que al estar vacío pues es 0 en una operación.

\


**== > Números a "string"**

1. A través del método `String()`

Llamar a la función string(), y dentro pasar la variable cuyo tipo de datos quieres cambiar

```javascript
var edad = 47;
String(edad);          //devuelve: "47" 
```

2. Con la sintaxis de notación por puntos `nombreVariable.toString()`;

```javascript
var edad = 47;
edad.toString();          //devuelve: "47" 
```

Ambos métodos funcionan por igual, pero quizá la tendencia es a usar la _**dot notation**_ o **notación por puntos** :`nombreVariable.toString()`\
La razón es que quizá sea algo más cómodo de usar.

\


**== > "string" a "números"**

_**USOS DE CAMBIO A NÚMEROS**_:\
Muchas aplicaciones de _JavaScript_ están basadas en **API**, lo que significa que se están comunicando con **el mundo exterior, y éste por lo general envía números como strings**, al utilizar un lenguaje llamado **notación de objetos** de _JavaScript_ . Recibiremos datos que **deberían ser números, decimales**, pero sin embargo están enviando como **strings**!!

\


Veamos las opciones que tenemos de conversion de **string** a **números** junto con su **sintaxis**:

```javascript
- Number(edad);
- parseInt("21.7");     // devuelve: 22 (número entero)
- parseFloat("21.7");   // devuelve: 21.7  (si necesitamos decimal, ésta es la opción)
```

Dependiendo de con qué comience, si con **número** o **string**:

```javascript
- parseInt("9999999 es mi número");      // devuelve:  9999999, ya que comienza con un número.
- parseInt("foo 9999999 es mi número");      // devuelve: NaN  (not a number) o sea, que no se puede convertir
```

Y también tenemos el llamado operator unario o _**unary operator**_, el signo de `+` delante de la variable. A veces recibes algún tipo de valor y sabes que será un **string**, pero es un **string** que en realidad debe ser un **número**, y dentro de ella **solo tienes que poner el signo más +**.

```javascript
edad = "40";
var nuevaEdad = +edad;     // (es muy típico guardar en una nueva variable)
console.log(nuevaEdad);  // devuelve: 40

```

\


**== > Booleanos a "números"**

`true` se convierte en **1** y `false` se convierte en **0**.

\


Esto es **muy útil** ya que todos los ordenadores y sistemas de todo el mundo utilizan **ceros y unos (código binario)**. Al final **todo lo que programamos** y hacemos se debe convertir en **ceros y unos**. Por ello resulta muy **útil** cuando necesitamos **revisar algo**.

_**EJEMPLO DE UN USO CONCRETO DE CONVERSIÓN DE BOOLEANOS EN 0 Y EN 1**_:

* Si estamos trabajando en un sistema que **no tiene realmente el concepto de VERDADERO o FALSO**, necesitamos devolver un **0** ó un **1**: ésta sería una manera rápida y eficiente de hacerlo. Sería el caso de que tengamos una función que se **comunica con alguna otra API**, y esta **API no sabe qué significa VERDADERO y FALSO** (no lo puede interpretar), **pero sí interpreta un 0 y un 1**, entonces lo podremos envolver como `true` o `false` , lo retornamos y todo funcionará.

\
\


## 3. ¿Cuáles son las tres funciones de String en JS?

3 funciones muy útiles para trabajar con datos tipo "**string**":

\


* 1 `.toLowerCase()` - `toUpperCase()` - . Devuelve el texto transformado a **minúsculas - mayúsculas** respectivamente:

```javascript
const text = "Las zonas verdes Pueden Protegerse.";

console.log(text.toLowerCase());   // "las zonas verdes pueden protegerse."
console.log(text.toUpperCase());   // "LAS ZONAS VERDES PUEDEN PROTEGERSE."
```

\
\


* 2 `.trim()` - `.trimEnd()` - `.trimStart()` Eliminador de espacios en blanco.\


\


EJEMPLO1: Eliminando espacios en blanco a ambos extremos:

```javascript
var prueba1 = "      borrando todos los espacios en blanco a los extremos       ";
console.log(prueba1.trim()); // devuelve: "borrando todos los espacios en blanco a los extremos"
```

\


EJEMPLO2: Eliminando los espacios del final:

```javascript
let text1 = "     ¡¡Hola!!     ";
let text2 = text1.trimEnd();
console.log(text2);      // devuelve:   "     ¡¡Hola!!"       (borra espacios al final)
```

\


EJEMPLO3: Eliminando los espacios del comienzo:

```javascript
let text1 = "     ¡¡Hola!!     ";
let text2 = text1.trimStart();
console.log(text2);      // devuelve: "¡¡Hola!!     "        (borra espacios del principio)
```

\
\


* 3 `.replace()`

Dentro del paréntesis si pone dos argumentos:

* el **primero** contiene la **información que quieres cambiar**
* el **segundo** contiene la información definitiva, el **cambio deseado**
* RESULTADO: cambiará el primer argumento por el segundo argumento, y lo hará solo en el **primer elemento coincidente**.

```javascript
let gracias = "¡Gracias por comprar en nuestra carnicería!";
let resultado = gracias.replace("carnicería", "tienda de deportes");
console.log(resultado);   // devuelve: "¡Gracias por comprar en nuestra tienda de deportes!"
```

\


CAMBIO DE **TODOS** LOS ELEMENTOS COINCIDENTES: **"GLOBAL"**.-

La función `.replace()` tiene una versión "**global**", que cambiaría todos los elementos coincidentes a la vez (no sólo el primero),\
a través de la **sintaxis** `(/arg1/g, arg2)`

```javascript
let texto = "no sé que es más gris, si el gris de tus ojos o el gris de las paredes de tu casa gris";
let resultado = texto.replace(/gris/g, "azul");
console.log(resultado);   

// devuelve: "no sé que es más azul, si el azul de tus ojos o el azul de las paredes de tu casa azul"
```

La `g`del primer argumento, el que deseamos cambiar, significa **GLOBAL**, y sin ella, de nuevo, sólo cambiaría el primer elemento coincidente.

\
\


## 4. ¿Qué es un condicional?

Nos da la posibilidad de ejecutar un proceso en el caso de que la **condición** que pongamos sea verdadera, y también en el caso de que ésta sea falsa.

\


**1. Sintaxis: utilizando `if` ("si"):**

* **1a).- SI ES IGUAL:**

a) Con dos signos de igual seguidos `==`. Esto comprueba sólo **el valor**:

```javascript
var1 = 16
var2 = ‘16’
if  (var1 =="Son iguales")
}
```

b) Mediante tres iguales `===` (_igual estricto_ o **strict equal**), comprueba también tanto **el valor** como **el tipo de dato**:

```javascript
if  (var1 === var2) {
console.log("Son exactamente iguales")
}
```

BUENAS PRÁCTICAS: Es muy raro utilizar solo los **dos iguales porque puedes obtener muchos errores**. Mejor utilizar siempre los tres iguales `===`.

\


*   **1b).- SI NO ES IGUAL**, tenemos dos opciones:    `!=` (no es igual a), que **comprueba el valor**    `!==` (no es igual a), **comprueba el valor y el tipo de datos** (modo **estricto**).

    \

* **1c).- SI ES MAYOR O IGUAL** `>=` son en realidad dos condiciones unidas por la disyuntiva “o”. **NO tiene una versión ‘estricta’** que compruebe **tipo de datos**, como en las anteriores.

```javascript
var edad = 25;
if (edad>= 25) {
  console.log("puedes conducir")
}        
// devuelve "puedes conducir"
```

\


**2. Sintaxis: utilizando `if/else`:**

* El `if`significa "en caso de que sí", en caso de que sea cierto o **true**.
* El `else`significa "en caso de que no", en caso de que sea **false**.

```javascript
var nota = 7;
if (nota >= 5) {
  console.log("puedes realizar el siguiente curso");
} else {
  console.log("tienes que hacer otra prueba");
} 
// devuelve:   "puedes realizar el siguiente curso"
```

\


**3. Sintaxis: utilizando `if / else / if`:**

Antes de poner ejemplos, mencionaremos que dentro de un `if`puede haber una **condición doble**. En el siguiente ejemplo se cumplen dos condiciones a la vez, y para unirlas utilizamos un doble ampersand **`&&`**, que significa "**y**":

```javascript
var puntos = 26;

if (puntos <= 10) {
  console.log("Puedes elegir un regalo de la lista 1");
 
} else if (puntos >= 11 && puntos <= 25) {
  console.log("Puedes elegir un regalo de la lista 2");
 
} else if (puntos > 25) {
  console.log("Elige tu regalo especial de la lista 3 y un vale sin caducidad");
}

// devuelve:  "Elige tu regalo especial en la lista 3 y un vale sin caducidad"

```

Hay que tener en cuenta de que **si no se cumple la condición**, simplemente IGNORA lo que hay dentro de las llaves {}.

\


**BUENAS PRÁCTICAS**:\
En vez del último `else-if` en la línea de código anterior , `else if (puntos > 25)`, podríamos haber puesto solamente `else`, pero si queremos ser más explícitos y también **asegurarnos de encontrar lo que buscamos**, es más conveniente la primera opción de `else-if`.

Imaginemos una situación en la que la variable `puntos` ni siquiera está puesta como **número** (por ejemplo, **string** u otro dato mal puesto), entonces con el `else` daría esa condición **como cierta**; sin embargo en realidad **sería un error**!! **Las buenas prácticas** nos dicen que mejor no echarlo todo al **"saco de todo el resto de situationes"** en el que se puede traducir los `else`. En este “saco” todo cabe, por lo que puede haber **efectos secundarios** no deseados.

Explicando este tema un poco más: esto sería como una pequeña **biblioteca de validaciones**: imaginemos que ponemos esto en un **programa web**, y que en esta tercera condición de `else if (puntos > 25)` ponemos simplemente `else` , y resulta que alguien no tiene `puntos`; se podría poner este caso como `null`. Si no, en vez de darnos un error o algo podríamos pensar (equivocadamente) que efectivamente se encuentra en la situación de `puntos > 25` , y por lo tanto imprimiría erróneamente:

```javascript
//"Elige tu regalo especial en la lista 3 y un vale sin caducidad"
```

\
\


## 5. ¿Qué es un operador ternario?

El **operador condicional ternario** es el único operador en _JavaScript_ que tiene **tres operandos**. Este operador se usa con frecuencia como atajo para la instrucción `if`.

El caso anterior en el tercer modo de sintaxis `if / if else / if else` se puede poner en una sola línea! Y quedaría así:

```javascript
puntos = 26
let progrPuntos = puntos <= 10 ? "Puedes elegir un regalo de la lista 1" : ((puntos >=11 && puntos <= 25) ? "Puedes elegir un regalo de la lista 2" : "Elige tu regalo especial de la lista 3 y un vale sin caducidad");

console.log(progrPuntos); // devuelve   "Elige tu regalo especial de la lista 3 y un vale sin caducidad"
```

Parece un poco confuso, pero en realidad puede ser bastante cómodo de codificar en algunas ocaciones.

* Detrás del signo de interrogacion `?` se pone la **condición verdadera**.
* Detrás del signo de dos puntos `:` se pone lo que sucede se la **condición es falsa**.
* Detrás de esos `:`repetimos el proceso de poner una **condición verdadera** `puntos >=11 && puntos <= 25`
* Finalmente, figura **si ninguna de las condiciones anteriores ha resultado verdadera**.

\


También se podría poner **sin los paréntsis finales**, así, aunque puede resultar **más confuso**:

```javascript
puntos = 26
let progrPuntos = puntos <= 10 ? "Puedes elegir un regalo de la lista 1" : (puntos >=11 && puntos <= 25) ? "Puedes elegir un regalo de la lista 2" : "Elige tu regalo especial de la lista 3 y un vale sin caducidad";

console.log(progrPuntos); // devuelve   "Elige tu regalo especial de la lista 3 y un vale sin caducidad"
```

\


Y también hay desarrolladores que lo prefieren **en varias líneas**:

```javascript
puntos = 26
let answer = puntos <= 10 
? "Puedes elegir un regalo de la lista 1" : (puntos >=11 && puntos <= 25) 
? "Puedes elegir un regalo de la lista 2" : "Elige tu regalo especial de la lista 3 y un vale sin caducidad";

console.log(answer); // devuelve   "Elige tu regalo especial de la lista 3 y un vale sin caducidad"
```

\


BUENAS PRÁCTICAS:\
Más que buenas prácticas se trataría de opiniones personales, pero el poner **paréntesis le da cierta claridad**, ya que envuelve perfectamente un concepto y ayuda a visualizar el código, **sin necesidad de escribir varias líneas**.

\
\


## 6. ¿Cuál es la diferencia entre una declaración de función y una expresión de función?

* Una función es un "subprograma" que **puede ser llamado por código externo** (o interno en caso de recursión) a la función.
* Al igual que el programa en sí mismo, **una función se compone de una secuencia de declaraciones**, que conforman el llamado **cuerpo de la función**.
* Se pueden **pasar valores** a una función, y la función **puede devolver un valor**.

\


#### 1. Declaración de una función

La creación de funciones por declaración probablemente sea **la forma más popular**. Esta forma permite declarar una función que existirá a lo largo de todo el código:

**SINTAXIS:**

* **comienza con la palabra `function`** seguida del **nombre de la variable** y los paréntesis:

```javascript
function saludar() {
  return "Hola";
}

console.log(saludar());      // devuelve: 'Hola'
console.log(typeof saludar); // devuelve: 'function'
```

Podríamos ejecutar la función `saludar()` **¡incluso antes de haberla creado!** y funcionaría correctamente, ya que _JavaScript_ **primero busca las declaraciones de funciones** y luego procesa el resto del código.

\


#### 2. Expresión de una función

Sin embargo, en _JavaScript_ es muy habitual el **«guardar funciones» dentro de variables**, para posteriormente **«ejecutar dichas variables»**. Se trata de un enfoque diferente: son las **funciones por expresión**, que fundamentalmente, hacen exactamente lo mismo (con algunos matices diferentes):

**SINTAXIS:**

```javascript
var saludo = function saludar() {
  return "Hola";
}

console.log(saludo()); // devuelve: 'Hola'
```

* El nombre de la función es **opcional**

Con este nuevo enfoque, estamos creando una función **en el interior de una variable**, lo que nos permitirá posteriormente **ejecutar la variable como si fuera una función** (que de hecho lo es, porque es lo que contiene).

Aquí, la función (_**saludar**_) pasa a ser inútil, ya que si intentamos ejecutar `saludar()` nos dirá que no existe. Sin embargo, cuando ejecutamos `saludo()` funciona correctamente. Ahora **el nombre de la variable pasa a ser el «nombre de la función»**, mientras que el anterior nombre de la función desaparece y se omite, creando un concepto llamado **funciones anónimas**.

\


#### 3. Diferencias de SINTAXIS entre la "declaración de una función" y la "expresión de una función".

**Declaraciones a la IZQUIERDA, Expresiones a la DERECHA**

La palabra reservada `function` se puede usar tanto al lado izquierdo como al lado derecho del signo igual **`=`**. Lo interesante de esto es que siguen **diferentes reglas dependiendo de dónde la escribimos**:

* Cuando la usamos al lado **IZQUIERDO**, estamos creando una **DECLARACIÓN DE FUNCIÓN** y es **obligatorio asignar un nombre**.

```javascript
// declaración de función
function soyUnaDeclaracion() {
  // ...
}
```

* En cambio, si la usamos a la **DERECHA** del símbolo igual, hablamos de una **EXPRESIÓN DE FUNCIÓN** (nombre opcional).

```javascript
// expresión de función
var soyUnaExpresion = function() {
  // ...
}
```

\


#### 4. Diferencias CLAVE entre "DECLARACIÓN DE FUNCIÓN" Y "EXPRESIÓN DE FUNCIÓN".

La diferencia fundamental es que las **funciones por expresión** es que estas últimas **sólo están disponibles A PARTIR DE la inicialización de la variable**. Si «ejecutamos la variable» antes de declararla, **nos dará un error** (o sea, **no** hay elevación o **hoisting** explicado más arriba en la **pregunta nº 1**)

O sea:

* Las **declaraciones de funciones son ascendidas** al momento de ejecución de nuestro programa, nuestra función se puede ejecutar incluso **antes de su definición**:

```javascript
nuevaFuncion()

function nuevaFuncion() {
  console.log("Hola Mundo!")
}

// devuelve:  Hola Mundo!
```

\


En cambio, esto **no es posible con las expresiones de funciones**, ya que no se sabe el valor que va a tener nuestra variable previamente declarada:

```javascript
nuevaFuncion() 

var nuevaFuncion = function nuevaFuncion() {
  console.log("Hola Mundo!");
}

//devuelve: Uncaught TypeError: nuevaFuncion is not a function 
```

\
\


Además, **dentro** de un bloque de código, como lo es un **objeto**, solo se pueden poner **las expresiones de función**, pero **no las declaraciones**:

a) Aquí no habría ningún problema:

```javascript
var age = 4;

if (age <= 10) {
  var buildMenu = function () {
    return "Kids' Menu";
  };

  console.log(buildMenu());  // devuelve "Kids's Menu""
 }
```

b) Pero si movemos la **declaración de función `greeting()`dentro del objeto del objeto** de la variable, nos daría un error: analizándolo en CodePen, nos diría que "las declaraciones de función no se deben poner en bloques", o sea, dentro de objetos, condicionales, etc. _JavaScript_ no lo permite:

```javascript
var age = 4;

if (age <= 10) {
  var buildMenu = function () {
    return "Kids' Menu";
  };
  //moviendo la declaración de la función dentro del objeto
  function wrongMenuBuilder () {
    return "Wrong Kids' Menu";
  }

console.log(buildMenu());
console.log(wrongMenuBuilder());   // causa el error mencionado
}
```

O sea que siempre que necesitemos crear funciones **dentro de un objeto, de una forma dinámica**, debemos utilizar las **expresiones de función**.

\
\


## 7. ¿Qué es la palabra clave "this" en JS?

* **`this`** en _JavaScript_ es una palabra clave muy utilizada dentro de funciones y clases, pues tiene **un valor flexible**. **`this`** significa _**esto**_ en español y, como su nombre indica, hace referencia al objeto en cuestión.
* La palabra clave **`this`** de una función se **comporta un poco diferente** en _JavaScript_ en comparación con otros lenguajes. Además tiene algunas diferencias entre el modo estricto y el modo no estricto.
* En general, el valor de **`this`** está determinado por **cómo se invoca a la función**.  **No puede ser establecida mediante una asignación en tiempo de ejecución**, y **puede ser diferente** cada vez que la función **es invocada**.

\


**a) `this` en contexto GLOBAL**

* En los navegadores este entorno suele ser el objeto _**window**_ y es accesible desde cualquier parte del código (excepto dentro de bloques cerrados, como funciones o módulos, sin un enlace explícito), y proporciona muchas propiedades y métodos útiles para interactuar con el navegador.Cuando se usa **`this`** en una función que no es llamada por ningún objeto, equivale este objeto **global** _**window**_ si estamos en un buscador o browser,
* **`this`** se refiere al **objeto globlal** si estamos en un entorno de ejecución de _JavaScript_ como _**Node.js**_ (plataforma que permite ejecutar código _JavaScript_ en el servidor). En los módulos individuales, **`this`** no apunta a global, sino a un objeto vacío ({}).

**Ejemplo1:**

```javascript
function prueba() {
  console.log(this);
}
// devuelve:  window
```

**Ejemplo2:**

```javascript
function saludar() {
  console.log("¡Hola!");
}
this.saludar(); // Llama a la función global `saludar`
```

\


**b) `this` en llamadas a métodos y como parte de un objeto**

* Si una función es **parte de un objeto**, se llama **método**, y si no lo está, sería una función propiamente dicha.
* Cuando una función es **llamada como método de un objeto**, su contexto de **`this`** se **asocia al objeto** que contiene el método.

**Ejemplo1 - estructura básica y sintaxis:**

```javascript
var objeto = {
  propiedad1: "valor",
  propiedad2: "valor2",
  
  metodo1() {
    console.log(this.propiedad1);
  }
};
```

\


**Ejemplo2:**

```javascript
var test = {
  etiqueta: 603,
  func: function () {
    return this.etiqueta;
  },
};

console.log(test.func());
// Devuelve: 603
```

Como podemos comprobar, dentro de una función, el valor de **`this`** está determinado **por el lugar en el que esa función es invocada**, es decir, se está refiriendo al **objeto mismo**. Veamos más ejemplos:

\


**Ejemplo3a:**

```javascript
const video = {
    titulo: 'sss',
    play() {
        console.log(this);
    }
};

video.play();

/*devuelve:
// [object Object] 
{
"titulo": "sss",
"play": play() {\n    console.log(this);\n  }
}*/

```

En este ejemplo, debido a que `play()` es un método **dentro del objeto video**, **`this`** hace referencia a ese **objeto mismo**.

Del mismo modo, podemos añadir un **método más tarde** y obtener el mismo resultado. Añadamos el método `video.stop()`:

\


**Ejemplo3b:**

```javascript
const video = {
    titulo: 'sss',
    play() {
        console.log(this);
    }
};

video.stop = function() {
  console.log(this);
}

video.stop();

/*devuelve:
// [object Object] 
{
  "titulo": "sss",
  "play": play() {\n    console.log(this);\n  },
  "stop": function () {\n  console.log(this);\n}
}
*/;
```

Vemos que la consola devuelve el **objeto `video`** de nuevo, ya que **`stop`** también es un método **dentro del objeto `video`**.

\


**Ejemplo4a:**

```javascript
var sammyboy = {
    nombre: 'Sammy',
    especie: 'gato',
    probar() {
        console.log(this.nombre);
        console.log(this === sammyboy);
    }
};
sammyboy.probar(); 
// "Sammy"
// true
```

Una vez más, comprobamos que hace referencia al objeto. Sin embargo es relativamente sencillo **perder el contexto** de **`this`**; si por ejemplo guardamos el **método en una función declarada para ejecutarla como tal** y no como un método (con su referencia al objeto), y añadimos:

**Ejemplo4b:**

```javascript
let probar = sammyboy.probar;
probar();
// devuelve: undefined
// devuelve: false

```

Aunque nos estamos refiriendo al método de un objeto, **la llamada** ocurre bajo la forma de una **función declarada en el ámbito global**.

***

## EJERCICIO PRÁCTICO CHECKPOINT 7

Cree una función JS que acepte 4 argumentos. Suma los dos primeros argumentos, luego los dos segundos y multiplícalos. Si el número creado es mayor que 50, la consola registra "¡El número es mayor que 50!". Si es más pequeño, la consola registra "¡El número es menor que 50!"\


**RESPUESTA:**

```javascript
function checkP7 (num1, num2, num3, num4) {
  sum1 = num1 + num2;
  sum2 = num3 + num4;
  multiplic = sum1 * sum2;
  if (multiplic > 50) {
    console.log("¡El número es mayor que 50!")  // 
  } else if (multiplic < 50) {
    console.log("¡El número es menor que 50!")
  }
}

checkP7 (1,2,3,4); M   // devuelve "¡El número es menor que 50!"
checkP7 (24,6,2,3);   // devuelve "¡El número es mayor que 50!"
```

***

***

\
\


OTRA OPCIÓN:

```javascript
function checkP7 (num1, num2, num3, num4) {
  sum1 = num1 + num2;
  sum2 = num3 + num4;
  multiplic = sum1 * sum2;
  multiplic > 50 ? console.log("¡El número es mayor que 50!") : (multiplic < 50 ? console.log("¡El número es menor que 50!") : null)
}

checkP7 (1,2,3,4); 
checkP7 (24,6,2,3);
```

OPCIONES TENIENDO EN CUENTA QUE PUEDE SER =50\
1\.

```javascript
function checkP7 (num1, num2, num3, num4) {
  sum1 = num1 + num2;
  sum2 = num3 + num4;
  multiplic = sum1 * sum2;
  if (multiplic > 50) {
    console.log("¡El número es mayor que 50!")
  } else if (multiplic < 50) {
    console.log("¡El número es menor que 50!")
  } else {
    console.log("Números incorrectos, por favor prueba de nuevo")
  }
}

checkP7 (50,2,3,4);
checkP7 (4,6,2,3);
```

2.

```javascript
function checkP7 (num1, num2, num3, num4) {
  sum1 = num1 + num2;
  sum2 = num3 + num4;
  multiplic = sum1 * sum2;
  multiplic > 50 ? console.log("¡El número es mayor que 50!") : (multiplic < 50 ? console.log("¡El número es menor que 50!"): console.log("Números incorrectos, prueba de nuevo")); 
}

checkP7 (50,2,3,4);
checkP7 (4,6,2,3);
```
