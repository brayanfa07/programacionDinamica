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
__

#####Algoritmo del cambio de monedas

___


```
public class calculoMonedas {
    private Moneda moneda1;
    private Moneda moneda2;
    private Moneda moneda3;
    private int acumulado;
    private int monedaActual;


    calculoMonedas(){
        moneda1 = new Moneda(7, 1);
        moneda2 = new Moneda(4, 1);
        moneda3 = new Moneda(3, 1);
        acumulado = 0;
        monedaActual = 1;
    }


    int calcularMonedas(int monto){

        Moneda monedas[] = {this.moneda1,this.moneda2, this.moneda3};
        for (int i = 0; i < monto; i++) {
            if ((((monedas[this.monedaActual].getCantidad() + 1) * monedas[this.monedaActual].getValor()) + acumulado) < monto) {
                monedas[this.monedaActual].setCantidad(monedas[this.monedaActual].getCantidad() + 1);
                this.acumulado = acumulado + monedas[monedaActual].getValor();
            }
            else if ((((monedas[this.monedaActual].getCantidad() + 1) * monedas[this.monedaActual].getValor()) + acumulado) > monto) {
                this.monedaActual = this.monedaActual + 1;
            }
            else{
                if ((((monedas[this.monedaActual].getCantidad() + 1) * monedas[this.monedaActual].getValor()) + acumulado) == monto) {
                   System.out.println("Su cambio son " + this.moneda1.getCantidad() + " moneda(s) de " + this.moneda1.getValor() +
                            " , " + this.moneda2.getCantidad() + " moneda(s) de " + this.moneda2.getValor() + " y " +
                            this.moneda3.getCantidad() + " moneda(s) de " + this.moneda3.getValor());
                    return 0;

                }
            }
        }
        System.out.println("Su cambio son " + this.moneda1.getCantidad() + " moneda(s) de " + this.moneda1.getValor() +
                " , " + this.moneda2.getCantidad() + " moneda(s) de " + this.moneda2.getValor()  + " y " +
                this.moneda3.getCantidad() + " moneda(s) de " + this.moneda3.getValor());
        return 0;
    }


    public static void main(String[] args) {
        calculoMonedas nuevo = new calculoMonedas();
        nuevo.calcularMonedas(21);
    }

}


class Moneda{
    int valor;
    int cantidad;


    Moneda(int valor1, int valor2){
        this.valor = valor1;
        this.cantidad = valor2;
    }

    public void setValor(int valor) {
        this.valor = valor;
    }

    public void setCantidad(int cantidad) {
        this.cantidad = cantidad;
    }

    public int getValor() {
        return valor;
    }

    public int getCantidad() {
        return cantidad;
    }
}

```





