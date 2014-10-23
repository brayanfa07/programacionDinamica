### Tecnológico de Costa Rica
#####Escuela de Ingeniería en Computación
#####IC3002 Análisis de Algoritmos - Prof. Mauricio Rojas
#####201157035 Brayan Fajardo Alvarado - Fecha: 23 de octubre de 2014
#####TAREA: Programación dinámica
___________
______________
__________
#####Programación dinámica
____
____
#####Algoritmo de Fibonacci
____
Este algoritmo consiste en ejecutar la sucesión de fibonacci para cierto número. Este tipo de ejercicio permite usar la programación dinámica ya que hace uso de las soluciones anteriores para la determinacion de fibobnacci de los números anteriores.
Ejp: 1, 1, 2, 3, 5, 8, 13, 21, 34...

Se presenta un primer caso, donde se hace uso de la recursión. Este algoritmo tiene un timpo de ejecución exponencial, el cual lo hace un poco deficiente.

```
public class Fibonacci {
    private int suma;
    private int contador;

    Fibonacci(){
        suma = 0;
        contador = 0;
    }

    int calcularFibonacci(int numero){
        contador = numero;
            if (numero == 0) {
                this.suma = suma + 0;
            } else if (numero == 1) {
                this.suma = suma + 1;
            } else {
                return calcularFibonacci(numero - 1) + calcularFibonacci(numero - 2);
            }
       System.out.println("Un número de la sucesión fibonacci es: " + this.suma);
       return suma;

    }
    public static void main(String[] args){
        Fibonacci fibonacci = new Fibonacci();
        System.out.println("Serie Fibonacci");
        fibonacci.calcularFibonacci(3);
    }
}
```

Pero a continuación se presenta otra solución, que reduce el tiempo de solución del algoritmo a un tiempo de O(1), ya que reduce la complejidad de volver a calcular el algoritmo, sino que toma en cuenta el valor de los últimos valores calculados.

```
class Fibonacci{

    private int cantidadFibonacci;

    Fibonacci(int numero){
        cantidadFibonacci = numero;
    }

    int calcularFibonacci(){
        int suma = 1;
        if (this.cantidadFibonacci < 1){
            suma = 0;
            System.out.println("El número Fibonacci para " + cantidadFibonacci + " es: " + suma);
            return suma;

        }
        if (this.cantidadFibonacci == 1) {
            suma = 1;
            System.out.println("El número Fibonacci para " + cantidadFibonacci + " es: " + suma);
            return suma;
        }
        else{
            int x = 1;
            int y = 1;
            for (int i = 2; i< this.cantidadFibonacci; i++){
                suma = x + y;
                y = x;
                x = suma;
            }
            System.out.println("El número Fibonacci para " + cantidadFibonacci + " es: " + suma);
            return suma;
        }
    }

    public static void main(String[] args){
        Fibonacci fibonacci = new Fibonacci(3);
        fibonacci.calcularFibonacci();
    }
}

```

