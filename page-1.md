# Page 1

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
