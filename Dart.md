![alt](https://imgs.search.brave.com/71ZpZYIDKJFF4hyzvZ_Ka3co-bXu5mS0uoIjcv5uvy4/rs:fit:1200:687:1/g:ce/aHR0cDovL3d3dy51/Y29sLm14L2NvbnRl/bnQvY21zLzkvaW1h/Z2UvVWRlQ0VDUlM4/MG4ucG5n)
#   *UNIVERSIDAD DE COLIMA*
## *FACULTAD DE INGENERIA MECANICA Y ELECTRICA*
#### *CARRERA: INGENIERIA EN COMPUTACION INTELIGENTE*
#### *Alumno: Christopher Kurt Alcantar Contreras*
#### *Profesor: Dr. Walter Alexander Mata López*
---

__Bienvenid@ a mi repositorio de github/Portafolio de segunda parcial__

En el obtendras todos los programas que realice en clases de programacion funcional

---
### Datos de tipado estatico
    //Tipado estatico: una vez que creo una variable, no puedo cambiar su valor.
    import 'dart:io';
    import 'dart:js_util';

    void main() {
    print("Hola mundo");
    //tipado explicito
    int miEntero = 10; //Para declarar variables la primer letra es minuscula
    double miDouble = 3.1416;
    print(miDouble is int);
    print(miEntero is double);

    num miNumero = 10;
    num miNumero2 = 3.1416;
    print(miNumero is int);
    print(miNumero2 is int);

    String miCadena = "hola";
    print(miCadena is String);

    dynamic miDinamico = "Hola";
    print(miDinamico);
    miDinamico = 3.1416;
    print(miDinamico);

    bool miBool = true;
    print(!miBool);
    }

---
 ### Runtyme- Tiempo de compilacion
     void main(List<String> args) {
      //declaracion de constante con tipo explicito
      //Tiempo de compilacion
      const double miPi =
          3.1416; // las constantes se asignan en tiempo de compilacion
      const double miGravedad = 9.81;
      //Asignando un valor en tiempo de ejecucion
      final double miPi;
      miPi = setPi();
      print(miPi);
      print(miGravedad);
    }

    double setPi() {
      //tiempo de ejecucion
      return 3.1416;
    }

    void main(List<String> args) {
      num miNumero;
      // Dynamic es un tipo de dato es para que le puedas asignar cualquier tipo de dato
      miNumero = 3.1416;

      print(miNumero.runtimeType); // Runtyme es el tiempo de ejecucion.
      //esto me regresara un dato tipo double.
    }

    void main() {
      var minumero1 = 100;
      var minumero2 = 9.81;
      var nombre = "kurt";
      print(minumero1.runtimeType);
      print(nombre.runtimeType);
    }

    void main() {
      var numero1 = 100;
      var numero2 = 9.81;

      var resultado; //no asigne ningun tipo de dato,
      //y al poner var me lo pone de tipo dinamico.

      resultado = numero1 + numero2;

      print(resultado.runtimeType); //Aqui nos damos cuenta que
      //que al poner runtime por
      //tiempo de ejecucion nos
      //retorna un valor double
    }

    void main() {
      const numero1 = 19.5;
      const numero2 = 10;
      //Final es para declarar una variable como entero.
      final total = numero1 * numero2;
      print(total);
    }

    void main() {
      //Impresion de numeros hexadecimales
      int nhex1 = 0xf;
      int nhex2 = 0xf;

      print(nhex1 * nhex2);
      var nOcatal = 125.toRadixString(8);
      print(nOcatal.runtimeType);

      var nh = 125.toRadixString(16);
      print(nh.runtimeType);
    }
---
### Interpolacion de cadenas 
    void main() {
      String nombreCurso = "Programacion Funcional";
      var num = 4;
      String carrera = "ici";
      //contetacion de cadenas
      print(carrera + " " + nombreCurso);
    //interpolaciond e cadenas
      print("$carrera $nombreCurso");
      // de esta forma es para funciones u operaciones aritmeticas
      print("${getCarrera}${nombreCurso}");
      print("el cuadrado de $num es ${num * num}");
      print("el cuadrado de $num es ${cuadrado(num)}");
    }

    String getCarrera() {
      return "ici";
    }

    int cuadrado(int num) {
      return num * num;
    }

    void main() {
      // de esta manera podemos imprimir  sin
      //necesidad de poner "," y si queremos hacerlo
      // en varios renglones "\n".
      print("En un lugar de la "
          "de la mancha de cuyo"
          "nombre no quiero acordarme");
    }

    void main() {
      print("Dame tu nombre");
      // Aqui obtenemos un dato a traves
      // del teclado.
      final nombre = stdin.readLineSync();
      print("Tu nombre es $nombre");
    }
 --- 
 ### Ciclos en Dart
 
    void main() {
      //listas con final
      final calificacion = [10, 6, 9, 8, 10, 8];
      // a pesar de ser de tipo final, al ser
      //listas se pueden agregar
      // elementos , pero si lo hacemos tipo
      //const no nos permitira agregar mas
      print(calificacion);
      //para agregar elementos a listas
      //tiene que ser del mismo tipo que es la lista.
      calificacion.add(2); // para agregar un elmento
      print(calificacion);
    //ciclos for en dart
      for (var i = 0; i < calificacion.length; i++) {
        print(calificacion[i]);
      }
    }
    void main(List<String> args) {
      for (var i = 1; i < 5; i++) {
        print("$i");
      }
      var numeros = [1, 2, 3, 4, 5];
      for (var e in numeros) {
        print("$e");
      }
    }

    void main() {
      var numeros = ["1", "2", 3.1415, true, 5];
      for (var e in numeros) {
        print("$e");
      }
      numeros.forEach((e) {
        print("$e");
      });
    }
---
### Condicionales if
    void main() {
      int n1 = 5, n2 = 3;
      if (n1 > n2) {
        print("$n1>$n2");
      } else if (n1 == n2) {
        print("$n1=$n2");
      } else {
        print("$n1<$n2");
      }
    }
---
### Operador ternario
    void main() {
      int n1 = 9, n2 = 4;
      int mayor;

      if (n1 < n2) {
        mayor = n1;
      } else {
        mayor = n2;
      }
      print("El mayor es: $mayor");

      int menor;
    //aqui se aplica un operador ternario donde
    //izquierda es verdadero y derecho falso
      n1 < n2 ? menor = n1 : menor = n2;
      print("El menor es: $menor");
      menor = n1 < n2 ? n1 : n2; //declarativo(funcional)
      print("El menor es $menor");
    }
---
### Sentencia Switch Case
    void main() {
      var dia;
      dia = 1;
      switch (dia) {
        case 1:
          print("el dia es ${getDay(dia)}");
          break;
        case "martes":
          print("hoy es martes");
          break;
        default:
          print("Dia no conocido");
      }
    }

    String getDay(int num) {
      if (num == 1) {
        return "lunes";
      } else {
        return " ";
      }
    }
 ---
 ### Listas
     void main() {
      var numeros = List<int>.generate(10, (i) => i + 1);
      print(numeros);
      var sum = 0;
      numeros.forEach((e) => sum += e);
      print(sum);
    }
---
### Casting sobre datos numericos 
    void main() {
      num a = 4;
      a as int; //Casting sobre datos numericos
      print(a.isEven);

      var infInt = 5;
      var infDouble = 9.81;
      print("${infInt.runtimeType}");
      print("${infDouble.runtimeType}");

      num infNum;
      infNum = 3.6;
      print("${infNum.runtimeType}");
      infNum = 5;
      print("${infNum.runtimeType}");
    }
      void main(List<String> args) {
      int a=5;
      double b=3.5;

      print(a.toDouble());
      print(b.toInt());
      print("el valor es "+a.toString());
      print("el valor es $a");
      print(a+b); //Casting implicito, si un dato es entero y el otro                         flotante el resultado es flotante.
      print(a/b);
    }
    void main(List<String> args) {
      var a = "5";
      var b = "8.5";

      print(int.parse(a) * 2);
      print(double.parse(b) * 2);

      var numero = 3.14161213123;
      print(numero.toStringAsFixed(3));
    }
    
---
### Funciones numericas
    void main() {
      int a = -3000;
      double b = 9.5;
      print(a.isNegative);
      print(b.floor());
      print(b.ceil());
      print(b.round());
      print(b.truncate());
      print(!b.isNaN);
    }
---
### Operaciones aritmeticas
    main() {
      //division
      print((10 / 3).truncate());
      print(10 / 3);
      print(cos(45 * pi / 180));
      print(sin(45 * pi / 180));
      print(pow(45, 180));
      print(max(45, 180));
      print(min(45, 180));
    }
 ---
 ### Incrementos y decrementos
     //INCREMENTOS
    void main(List<String> args) {

     var contador=0;

     contador=contador+1;
     print(contador);
     contador+=1;
     print(contador);
     contador++;
     print(contador);
     ++contador;
     print(contador);

     var c=10;
     print(++c);//11
     c=10;
     print(c++); //10
     print(c);
    }
    // DECREMENTOS
    void main(List<String> args) {

      var contador = 0;

      contador = contador - 1;
      print(contador);
      contador -= 1;
      print(contador);
      contador--;
      print(contador);
      --contador;
      print(contador);

      var c = 10;
      print(--c); //11
      c = 10;
      print(c--); //10
      print(c);
    }
 ---
 ### Clases y constructores
       void main() {
        User usuario = User("Kurt", 15);
        print(usuario);
        usuario.reporteUser();
        print(usuario.nombre);
        print(usuario.edad);
        usuario.nombre = "Kurt";
        usuario.edad = 18;

        User usuario2 = User();
        usuario2._nombre = "Olga";
        usuario2.edad = 19;
        usuario2.reporteUser();
      }

      //clase es una especie de cascaron.

      //Clase que reperesenta un usueario
      class User {
        //Siempre la primera letra del nombre de la clase es en mayuscula
        ///Propiedad de nombre de tipo string
        String? _nombre;

        ///Propiedad edad de tipo int
        int? _edad;

        ///metodo que imprime un usuario
        void reporteUser() {
          print(_nombre);
          print(_edad);
        }

        User(String nombre, int edad) {
          this._nombre = nombre;
          this._edad = edad;
        }

        void set nombre(String nombre) => _nombre = nombre;
        String get nombre => _nombre!;
        void set nombre(String nombre) {
          _nombre = nombre;
        }

        void set edad(int edad) {
          _edad = edad;
        }
        void set edad(int edad) => _edad = edad; //=> ES UN FAT ARROW
        int get edad => _edad!;
        String get nombre {
          return _nombre!; // "!" ES PARA OBLIGAR A RETORNAR UN VALOR.
            }
         }
---
### Clases y constructores con metodos get y setter v1
    void main() {
      User usuario = User(nombre: "Kurt", edad: 15);
      print(usuario.getNombre);
      print(usuario.getEdad);
    }

    class User {
      String? nombre;
      int? edad;
      void reporteUser() {
        print(nombre);
        print(edad);
      }

      User({this.nombre, this.edad});

      void set setnombre(String nombre) => nombre = nombre;
      void set setedad(int edad) => edad = edad; //=> ES UN FAT ARROW
      String get getNombre => nombre!;
      int get getEdad => edad!;
    }
 --- 
 ### Clases y constructores con metodos get y setter v2
     void main() {
      User usuario = User.nombre("Kurt");
      User usuario2 = User.edad(15);
      usuario.reporteUser();
      usuario2.reporteUser();
    }

    class User {
      String? nombre;
      int? edad;
      void reporteUser() {
        print(nombre);
        print(edad);
      }

      User.nombre(this.nombre);
      User.edad(this.edad);
      void set setNombre(String nombre) => nombre = nombre;
      void set setEdad(int edad) => edad = edad; //=> ES UN FAT ARROW
      String get getNombre => nombre!;
      int get getEdad => edad!;
    }
 --- 
 ### Clases y constructores con metodos getter y setter v3
     void main() {
      User usuario = User.nombre("Kurt");
      User usuario2 = User.edad(15);
      print(usuario.getNombre);
      print(usuario2.getEdad);
    }

    class User {
      String? _nombre;
      int? _edad;
      void reporteUser() {
        print(_nombre);
        print(_edad);
      }

      User.nombre(String nombre) {
        this._nombre = nombre;
        this._edad = 0;
      }
      User.edad(int edad) {
        this._edad = edad;
        this._nombre = "-";
      }
      void set setNombre(String nombre) => nombre = nombre;
      void set setEdad(int edad) => edad = edad; //=> ES UN FAT ARROW
      String get getNombre => _nombre!;
      int get getEdad => _edad!;
    }
---
### Pre- Examen, manejo de constructores, clases, metodo getter y setters

    void main() {
      Vehiculo miNave = Vehiculo(4, "rojo", "ferrari", "2022");
      print(miNave.getllantas);
      print(miNave.getColor);
      print(miNave.getMarca);
      print(miNave.getModelo);

      miNave.estacionar();
      miNave.encenderr();
      miNave.frenar();
    }

    class Vehiculo {
      int? _nollantas;
      String? _marca;
      String? _modelo;
      String? _color;
      String? _automovil;

      void estacionar() {
        print("Estacionar");
      }

      void frenar() {
        print("Frenando");
      }

      void encenderr() {
        print("Encendido");
      }

      Vehiculo(int llantas, String color, String marca, String modelo) {
        this._nollantas = llantas;
        this._color = color;
        this._marca = marca;
        this._modelo = modelo;
      }

      void set setLlantas(int llantas) => _nollantas = llantas;
      int get getllantas => _nollantas!;

      void set setMarca(String marca) => _marca = marca;
      String get getMarca => _marca!;

      void set setModelo(String modelo) => _modelo = modelo;
      String get getModelo => _modelo!;

      void set setColor(String color) => _color = color;
      String get getColor => _color!;
    }

 


 
 
 
 
