### Ejemplos de objetos, clases y métodos
~~~
void main(){
  Operacion operacion = Operacion(); 
  operacion.num1 = 2.0; 
  operacion.num2 = 4.0;
  print('La suma es : ${operacion.suma()}');
  operacion.resta();
  print('La multiplicación es : ${operacion.multiplicacion()}');
}
class Operacion{
  double? num1; 
  double? num2;
  
  double suma(){
    double s = num1! + num2!;
    return s;
    
  }
  void resta(){
    double r = num1! - num2!;
    print('La resta es: $r');
      
  }
  double multiplicacion(){
    double m = num1! * num2!;
    return m;
    
  }
}
~~~

### Ejemplos de constructores
~~~
void main(){
  Person person = Person(n: "Tatiana", s: "F");
   
    person.apellido = " Torres";
    person.edad = 18;
    print('El nombre es: ${person.nombre}');
    print('El apellido es:${person.apellido}');
    print('El sexo es: ${person.sexo}');
    print('El nombre completo es: ${person.nombreCompleto()}');
    print('La edad es: ${person.edad}');
    person.edadMas(10);
} 
class Person{
  String? nombre, sexo, apellido;
  int? edad;
  
  Person ({String? n, String? s}){
    sexo = s;
    nombre = n;
  }
  String nombreCompleto(){
    String nC = nombre! + apellido!;
    return nC;
  }
  void edadMas(int eM){
    int i = edad! + eM;
    print('La edad sumada es: $i');
  }
    
}
~~~

### Ejemplo de herencia con clase animales
~~~
void main() {
  Conejo conejo = Conejo();
  conejo.tipoAnimal = 'Viviparos';
  conejo.alimento = 'Plantas';
  conejo.bioma = 'Praderas secas y cubiertas de matorrales';
  Hiena hiena = Hiena();
  hiena.tipoAnimal = 'Viviparos';
  hiena.alimento = 'Carne';
  hiena.bioma = 'Sabanas, matorrales y desiertos';
  Leon leon = Leon();
  leon.tipoAnimal = 'Viviparos';
  leon.alimento = 'Carne';
  leon.bioma = 'Sabanas africanas';
  Humano humano = Humano();
  humano.tipoAnimal = 'Viviparos';
  humano.alimento = 'Carnes y plantas';
  humano.bioma = 'Casas, viviendas y refugios';
  print("""
  ANIMALES
  
  Conejo
  
  Son animales ${conejo.tipoAnimal}, es decir, se desarrollan
  dentro del utero.
  Su habitad son las ${conejo.bioma}.
  
  Hiena
  
  Son animales ${hiena.tipoAnimal}, es decir, se desarrollan
  dentro del utero.
  Su habitad son las ${hiena.bioma}.
  
  Leon
  
  Son animales ${leon.tipoAnimal}, es decir, se desarrollan
  dentro del utero.
  Su habitad son las ${leon.bioma}.
  
  Humano 
  
  Son animales ${humano.tipoAnimal}, es decir, se desarrollan
  dentro del utero.
  Su habitad son las ${humano.bioma}.
  """);
}

class Animal{
  String? tipoAnimal;
}
class Herbivoro extends Animal{
  String? alimento;  
}
class Carnivoro extends Animal{
  String? alimento;  
}
class Omnivoro extends Animal{
  String? alimento;  
}
class Conejo extends Herbivoro{
  String? bioma;  
}
class Leon extends Carnivoro{
  String? bioma;  
}
class Hiena extends Carnivoro{
  String? bioma; 
}
class Humano extends Omnivoro{
  String? bioma; 
}
~~~

### Método static
~~~
void main() {
  
  Vaca vaca = Vaca();
  vaca.emitirSonido();
  
  Gato gato = Gato();
  gato.emitirSonido();
  
  Perro perro = Perro();
  perro.nombre="Teo";
  print("El nombre del perro es: ${perro.nombre}");
  perro.emitirSonido();
  
  Carnivoro.imc(10,5);
}

abstract class Animal{
  void emitirSonido();
}

class Vaca implements Animal{
  @override
  void emitirSonido(){
    print("El sonido de la vaca es: Muu");
  }
}  
class Gato implements Animal{
  @override
  void emitirSonido(){
    print("El sonido del gato es: Miau");
  }
}

class Carnivoro {
 String? nombre;
 
 static void imc(int altura, int peso){
   print("El indice de masa corporal es ");
   print(peso * altura);
 }
}

class Perro extends Carnivoro implements Animal{
  @override
  void emitirSonido(){
    print("El sonido del perro es: Woof");
  }
}
~~~