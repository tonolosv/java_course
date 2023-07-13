# Introduccion a Java

## Un poco de historia

La facilidad que Java presenta al ser multiplataforma, hace que este lenjuage sea cotizado y con gran demanda en el mercado de programacion.

En 1990 Sun Microsystems liderados por James Gosling junto a sus colegas trabajaron en un proyecto que lo denominaron "Proyecto Verde", con la intencion de desarrollar tecnologia que se usaria en dispositivos inteligentes y domesticos. Asi que modificaron y extendieron C++, pero fue lo esperado.
Por ello se creo el proyecto "OAK" que contenia funcionabilidades de C, C++ y Objective C, dando el nacimiento de Java, el cual se llamo de esa manera por asuntos de propiedad intelctual.

---

## 1.1 Metodo Main

Para iniciar o ejecutar un programa en Java, es el metodo _main()_. El compilador de Java o JVM busca este metodo principal cuando empieza la ejecucion, y su firma tiene que ser reconocida desde el punto de entrada, de lo contrario no inicia el proyecto.
La ejecucion del programa Java se llama `java.exe`, el cual realiza llamadas de Java Native Interface o JNI y cargan la JVM; `java.exe` analiza la linea de comando, genera un matriz de cadenas e invoca el metodo _main()_. El proceso deamon se adjunta al metodo principal y este a un subproceso se destruye solo cuando el programa Java detiene la ejecucion

![Java Main](/img/Group2-660x330.jpg)

#### Estructura del metodo Main()

```java
class saludando{
    public static void main(String[] args){
        System.out.println("Hola a todos")
    }
}

Output:
Hola a todos
```

- public: Modificador de acceso, que especifica desde donde y quien puede acceder al metodo. _public_ da disponibilidad global, y se hace de esa manera para que la JVM pueda invocarlo desde fuera de la clase.

- Static: es una **palabra clave** que esta asociada a un metodo, lo que lo convierte en un metodo relacionado con la clase. El método _main()_ es estático para que JVM pueda invocarlo sin instanciar la clase, ahorra el desperdicio innecesario de memoria que habría sido utilizada por el objeto declarado solo para llamar al metodo _main()_ por la JVM

- void: **palabra clave** y sirve para especificar que un metodo no devolvera nada, ya que el metodo _main()_ no devuelve nada, su tipo de retorno es void. Cuando finaliza el metodo _main()_ se detiene el programa de Java; no hay retorno al metodo.

- main(): Nombre del metodo principal de Java. Es el identificador que busca la JVM como punto de partida del programa java. <u>Ojo no es una palabra clave</u>.

- String[] args: Almacena argumentos de linea de comandos de Java y es una matriz de tipo _java.lang.String_ class. Esa es la razón porque se llama _array string_ pero no esta fijo porque el usuario puede usarlo en cualquier nombre en su lugar

```java
class GeeksforGeeks {
	public static void main(String[] args)
	{
		for (String elem : args)
			System.out.println(elem);
	}
}

output
1
2
3
```

## 1.2 Constantes y tipos de datos

Los datos que se presentaran son datos de _Estructuras Primarias_, su caracteristica es manejar <u>un solo valor</u> en el tiempo

### 1.2.1 Constantes

Es un <u>valor inalterable en el tiempo</u>, y sirve para realizar calculos. Ejecutado el programa no se puede cambiar dicho valor.

Sintaxis

```java
static final nombreConstante = valor;
```

> [!CONSIDERESE]
>
> static final: establece como un valor constante
>
> nombreConstante: nombre de esa variable
>
> valor: dato ingresado

Ejemplo:
Se hara una aplicacion del IVA, la variable `imp` eb
l cual es un valor que no cambia y utilizando `double`, como tipo de dato.

```java
public class factura{
  static final double imp = 0.13;
    static double impuesto (double monto)
    {
      return monto * imp;
    }
}
```

### 1.2.2 Variables

Es un valor que tiene un cambia durante la ejecucion de un programa, estas pueden ser de diferentes tipos

#### Datos enteros

Se utilizan como enteros sin signos, los tipos mas comunes son: int o long, dependendiendo de la presicion que se desea, por ello se debe destacar en el nombre de la variable

| TIPO DE DATO | TAMAÑO            | RANGO                                       |
| :----------: | :---------------- | :------------------------------------------ |
|     byte     | 1 byte (8 bytes)  | -128 to 127                                 |
|    short     | 2 bytes (16 bits) | –32768 to 32767                             |
|     int      | 4 bytes (32 bits) | –2147483648 to 2147483647                   |
|     long     | 8 bytes (64 bits) | –9223372036854775808 to 9223372036854775807 |

#### Literales Enteros

- Decimales: Numeros ordinarios sin ninguna notacion especial
- Hexadecimal: Base 16 c/u notacion 0x o 0X, similar a C, C++
- Octal: Representados mediante un 0 incial, antecediendo a los digitos

```java
public class Enteros {
    public static void main(String[] args) {
        {
      byte dato1 = 1;
      short dato2 = 100;
      int dato3 = 1000;
      long dato4 = 10000000;

      System.out.println("Dato tipo byte " + String.valueOf(dato1));
      System.out.println("Dato tipo entero corto " + String.valueOf(dato2));
      System.out.println("Dato tipo largo " + String.valueOf(dato3));
      System.out.println("Dato tipo byte " + String.valueOf(dato4));
        }

    }
}
```

Resultado

![Literales enteros](/img/literalesEnteros.png 'Respuesta')

#### Dato como flotante

Representan numeros como partes fraccionarias

- float: 4 bytes | 32 bits
- double: 8 bytes | 64 bits

#### Literales en coma flotante

Numeros con partes fraccionarias que pueden representarse con notacion estandar o cientifica.

- float: 4 bytes | 32 bits
- double: 8 bytes | 64 bits

```java
double PI = 314.16E-2;  // Valor de Pi
float tempDia = (float) 29.6; // temperatura del dia
```

Resultado

![Literales de coma flotante](/img/comaFlotante.png 'Respuesta')

#### Dato Boolean

Representan estados de valor: True o False

```java
public class Booleanos {
    boolean verificar (int numero){
        boolean aux = false;
        if (numero > 0)
            aux = true;
        return aux;
    }
}
```

#### Dato String (cadena)

Almacena y procesa estrictamente texto y son considerados como objetos, para usar este tipo de dato se debe anteponer la palabra reservada `String`.

Diferentes formas de escribir una cadena

```java
public class cadenas {
    public static void main(String[] args) {
        String texto = "Hola Moe";
        String s = new String("Hola Mundo");
        String pais = new String();
        pais = "Nicaragua";

        System.out.println(pais);
        System.out.println(texto);
        System.out.println("opcion de mensaje = " + s);

    }
}
```

Resultado

![String o cadenas](/img/cadena.png)

Para tener un panorama mas amplio de como estan estructurados los datos Primarios, se esquematizan en la siguiente imagen

![Estructura](/img/estructura.png)

## 1.3 Vectores y Matrices

Que pasaria si se desean almacenar al mismo tiempo 5 o miles de datos que pertenecen al mismo tipo, no seria adecuado crear esa cantidad de variables, porque se tendrían anomalías en la lectura, almacenamiento, desempeño, etc.
Una de las alternativas que se poseen son los `vectores` siendo una estructura unidimensional donde se pueden registrar valores del mismo tipo de dato.

```java
public class vectores {
    public static void main(String[] args) {
        int vector [] = new int[5];
        String nombres [] = {"Joe", "Juan", "Pedro"};
        vector[0]= 5; vector[1]= 25; vector[2]= 3; vector[3]= 46; vector[4]= 1;

        System.out.println("Datos de la posicion 2 es: " + String.valueOf(vector[1]));
        System.out.println("Datos de la posicion 2 es: " + nombres[1]);
    }
}
```

> int vector [] = new int [5] // indica que aceptara solamente 5 valores
>
> String nombres [] = {"Joe", "Juan", "Pedro"}; // el espacio por el momento es de 3 valores
>
> el inicio contable de un vector siempre es _0_.

Resultado

![Vectores](/img/vectores.png 'vectores')

### 1.3.2 Matrices

Es una coleccion de celdas bidimensionales, donde se pueden almacenar valores del mismo tipo en ambas direcciones filas y columnas.

```java
public class pruebaMatriz{
    public static void main(String [] args){
        int matriz [][] = new int [3][4];
        matriz [0][0] = 15 ; matriz [1][0] = 24; matriz [2][0] = 38;
        matriz [0][1] = 17 ; matriz [1][1] = 64; matriz [2][1] = 83;
        matriz [0][2] = 65 ; matriz [1][2] = 33; matriz [2][2] = 28;
        matriz [0][3] = 28 ; matriz [1][3] = 17; matriz [2][3] = 99;
        systems.out.println("Contenido " + matriz [2][0]);
        systems.out.println("Contenido " + matriz [0][3]);
    }
}
```

El codigo anterior demuestra la construccion de una matriz de 3 columnas y 4 filas. Las posiciones se empieza en [0][0], para determinar el tamaño se puede hacer uso de length.

Resultado

![Matrices](/img/matriz.png 'Matrices')

### 1.3.3 Colecciones

Es una referencia a un grupo de objetos (tipo Object), donde se almacena cualquier _objeto_ en una coleccion para poder acceder y se requiere de un casting^1 para acceder a ellos. Pueden cambiar el tamaño de la coleccion en forma dinamica, ordenarse, insertar o borrarse los _objetos_.

- **ArrayList**: Permite almacenar datos en memoria de forma equivalente a los arrays, una ventaja no es necesaria declarar su tamaño. Incrementa o disminuye sus elementos de manera dinamica, independiente del indice y este se puede encontrar en el paquete `java.util`.

  ```java
  import java.util.ArrayList;

  public class Main {
   public static void main(String[] args) {
      ArrayList<String> cars = new ArrayList<String>();
      cars.add("Volvo");
      cars.add("BMW");
      cars.add("Ford");
      cars.add("Mazda");
      System.out.println(cars);
  } }

    output
    [Volvo, BMW, Ford, Mazda]

  ```

- **vector**: coincidente al _ArrayList_ los metodos que aplica se sincronizan mediante al uso de multihilos seguros, pertenecientes al paquete `java.util.package`. Su crecimiento es dimanica por lo que puede crecer o decrecer dinamicamnente

  ```java
  import java.util.Vector;

  class Main {
      public static void main(String[] args) {
          Vector<String> mammals= new Vector<>();

          // Using the add() method
          mammals.add("Dog");
          mammals.add("Horse");

          // Using index number
          mammals.add(2, "Cat");
          System.out.println("Vector: " + mammals);

          // Using addAll()
          Vector<String> animals = new Vector<>();
          animals.add("Crocodile");

          animals.addAll(mammals);
          System.out.println("New Vector: " + animals);
      }
  }

  output
  Vector: [Dog, Horse, Cat]
  New Vector: [Crocodile, Dog, Horse, Cat]
  ```

---

[:leftwards_arrow_with_hook: menu principal](/README.md)
