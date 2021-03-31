# EjerciciosJava
Algunos ejercicios varios de Java
/*--------------------------------------------------------------------------------*/
Ejercicio 10
Escribe un programa que genere 20 números enteros aleatorios entre 0 y 100
y que los almacene en un array. El programa debe ser capaz de pasar todos
los números pares a las primeras posiciones del array (del 0 en adelante) y
todos los números impares a las celdas restantes. Utiliza arrays auxiliares si
es necesario.
/*--------------------------------------------------------------------------------*/

package repasoHastaSockets;

public class random_shit1 {

	public static void main(String[] args) {

		int indice = 0;
		int indiceFin = 19;
		int arr1[] = new int[20];
		int arr2[] = new int[20];
		for (int i = 0; i < arr1.length; i++) {
			arr1[i] = (int) (Math.random() * (100 - 0 + 1) + (0));
		}
		System.out.println("Arreglo inicial");
		for (int i : arr1) {
			System.out.print(i + " - ");
		}

		for (int i = 0; i < arr1.length; i++) {
			if (arr1[i] % 2 == 0) {
				arr2[indice] = arr1[i];
				indice++;
			} else {
				arr2[indiceFin] = arr1[i];
				indiceFin--;
			}
		}
		System.out.println("");
		System.out.println("Arreglo final");
		for (int i : arr2) {
			System.out.print(i + " - ");
		}
	}
}
/*--------------------------------------------------------------------------------*/
Ejercicio 13
Escribe un programa que rellene un array de 100 elementos con números ente-
ros aleatorios comprendidos entre 0 y 500 (ambos incluidos). A continuación
el programa mostrará el array y preguntará si el usuario quiere destacar el
máximo o el mínimo. Seguidamente se volverá a mostrar el array escribiendo
el número destacado entre dobles asteriscos.
Ejemplo:
459 204 20 250 178 90 353 32 229 357 224 454 260 310 140 249 332 426 423 413 96 447 465 29\
8 459 411 118 480 302 417 42 82 126 82 474 362 76 190 104 21 257 88 21 251 6 383 47 78 392\
394 244 494 87 253 376 379 98 364 237 13 299 228 409 402 225 426 267 330 243 209 426 435 \
309 356 173 130 416 15 477 34 28 377 193 481 368 466 262 422 275 384 399 397 87 218 84 312\
480 207 68 108
¿Qué quiere destacar? (1 – mínimo, 2 – máximo): 1
459 204 20 250 178 90 353 32 229 357 224 454 260 310 140 249 332 426 423 413 96 447 465 29\
8 459 411 118 480 302 417 42 82 126 82 474 362 76 190 104 21 257 88 21 251 **6** 383 47 78\
392 394 244 494 87 253 376 379 98 364 237 13 299 228 409 402 225 426 267 330 243 209 426 \
435 309 356 173 130 416 15 477 34 28 377 193 481 368 466 262 422 275 384 399 397 87 218 84\
312 480 207 68 108
/*--------------------------------------------------------------------------------*/
import java.util.Scanner;

public class random_shit1 {

	public static void main(String[] args) {

		int max = 500;
		int min = 1;
		int arreglo[] = new int[500];
		int contador = 0;
		int menor = 501;
		int mayor = 0;
		Scanner sn = new Scanner(System.in);

		for (int i = 0; i < arreglo.length; i++) {
			arreglo[i] = (int) (Math.random() * (max - min + 1) + (min));
		}
		for (int i = 0; i < arreglo.length; i++) {
			System.out.print(arreglo[i] + " ");
			contador++;
			if (contador % 30 == 0) {
				System.out.println("");
			}
			if (arreglo[i] < menor) {
				menor = arreglo[i];
			}
			if (arreglo[i] > mayor) {
				mayor = arreglo[i];
			}
		}
		System.out.println("");
		System.out.println("***************************************************************");
		System.out.println("Mayor(1) / Menor(2)");
		System.out.println("***************************************************************");
		int decision = sn.nextInt();
		for (int i = 0; i < arreglo.length; i++) {
			contador++;
			if (contador % 30 == 0) {
				System.out.println("");
			}
			if (decision == 1) {
				if (arreglo[i] == mayor) {
					System.out.print("**" + arreglo[i] + "**");
				} else {
					System.out.print(arreglo[i] + " ");
				}
			} else if (decision == 2) {
				if (arreglo[i] == menor) {
					System.out.print("**" + arreglo[i] + "**");
				} else {
					System.out.print(arreglo[i] + " ");
				}
			}
		}

	}

}
/*--------------------------------------------------------------------------------*/
Ejercicio 15
Un restaurante nos ha encargado una aplicación para colocar a los clientes en
sus mesas. En una mesa se pueden sentar de 0 (mesa vacía) a 4 comensales
(mesa llena). Cuando llega un cliente se le pregunta cuántos son. De momento
el programa no está preparado para colocar a grupos mayores a 4, por tanto,
si un cliente dice por ejemplo que son un grupo de 6, el programa dará el
mensaje “Lo siento, no admitimos grupos de 6, haga grupos de 4
personas como máximo e intente de nuevo”. Para el grupo que llega,
se busca siempre la primera mesa libre (con 0 personas). Si no quedan mesas
libres, se busca donde haya un hueco para todo el grupo, por ejemplo si el
grupo es de dos personas, se podrá colocar donde haya una o dos personas.
Inicialmente, las mesas se cargan con valores aleatorios entre 0 y 4. Cada
vez que se sientan nuevos clientes se debe mostrar el estado de las mesas.
Los grupos no se pueden romper aunque haya huecos sueltos suficientes. El
funcionamiento del programa se ilustra a continuación:
Ejemplo:
┌─────────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│Mesa no │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │
├─────────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│Ocupación│ 3 │ 2 │ 0 │ 2 │ 4 │ 1 │ 0 │ 2 │ 1 │ 1 │
└─────────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
¿Cuántos son? (Introduzca -1 para salir del programa): 2
Por favor, siéntense en la mesa número 3.
┌─────────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│Mesa no │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │
├─────────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│Ocupación│ 3 │ 2 │ 2 │ 2 │ 4 │ 1 │ 0 │ 2 │ 1 │ 1 │
└─────────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
¿Cuántos son? (Introduzca -1 para salir del programa): 4
Por favor, siéntense en la mesa número 7.
┌─────────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│Mesa no │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │
├─────────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│Ocupación│ 3 │ 2 │ 2 │ 2 │ 4 │ 1 │ 4 │ 2 │ 1 │ 1 │
└─────────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
¿Cuántos son? (Introduzca -1 para salir del programa): 3
Tendrán que compartir mesa. Por favor, siéntense en la mesa número 6.
┌─────────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│Mesa no │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │
├─────────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│Ocupación│ 3 │ 2 │ 2 │ 2 │ 4 │ 4 │ 4 │ 2 │ 1 │ 1 │
└─────────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
¿Cuántos son? (Introduzca -1 para salir del programa): 4
Lo siento, en estos momentos no queda sitio.
┌─────────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│Mesa no │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │
├─────────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤
│Ocupación│ 3 │ 2 │ 2 │ 2 │ 4 │ 4 │ 4 │ 2 │ 1 │ 1 │
/*--------------------------------------------------------------------------------*/
import java.util.Scanner;

public class random_shit1 {

	public static void main(String[] args) {
		System.out.println("¿Cuántos son? (Introduzca ' -1 ' para salir del programa)");
		Scanner sn = new Scanner(System.in);
		int decision = sn.nextInt();
		sn.close();
		if (decision != -1) {
			boolean salir = false;
			int contador = 0;
			System.out.println();
			int arr1[] = new int[10];
			for (int i = 0; i < arr1.length; i++) {
				arr1[i] = (int) (Math.random() * (4 - 0 + 1) + (0));
			}

			for (int i = 0; i < arr1.length; i++) {
				System.out.println("Mesa" + (i + 1) + ": " + arr1[i]);
			}

			if (decision > 4) {
				System.out.println("Lo siento, no admitimos grupos de " + decision + ". Haga grupos de 4"
						+ " personas como máximo e intente de nuevo");
			} else {
				System.out.println("Puede ubicarse en la mesa: ");
				while (!salir) {
					if (arr1[contador] + decision <= 4) {
						System.out.println(contador + 1);
						salir = true;
					}
					contador++;
					if (contador >= arr1.length) {
						salir = true;
						System.out.println("No hay lugar disponible");
					}
				}
			}
		} else {
			System.out.println("Hasta luego");
		}

	}

}
/*--------------------------------------------------------------------------------*/
Ejercicio 16
Escribe un programa que rellene un array de 20 elementos con números ente-
ros aleatorios comprendidos entre 0 y 400 (ambos incluidos). A continuación
el programa mostrará el array y preguntará si el usuario quiere resaltar los
múltiplos de 5 o los múltiplos de 7. Seguidamente se volverá a mostrar el
array escribiendo los números que se quieren resaltar entre corchetes.
Ejemplo: “‘console
159 204 20 250 178 90 353 32 229 357 224 54 260 310 140 249 335 326 223
13 ¿Qué números quiere resaltar? (1 – los múltiplos de 5, 2 – los múltiplos de
7): 1 159 204 [20] [250] 1
/*--------------------------------------------------------------------------------*/
import java.util.Scanner;

public class random_shit1 {

	public static void main(String[] args) {

		int array[] = new int[20];
		
		for (int i = 0; i < array.length; i++) {
			array[i] = (int) (Math.random() * (400 - 0 + 1) + (0));
		}
		for (int i : array) {
			System.out.print(i + " ");
		}
		System.out.println("");
		System.out.println("¿Qué números quiere resaltar? (1 – los múltiplos de 5, 2 – los múltiplos de " + "7):");
		Scanner sn = new Scanner(System.in);
		int decision = sn.nextInt();
		if (decision == 1) {
			for (int i = 0; i < array.length; i++) {
				if (array[i] % 5 == 0) {
					System.out.print(" [" + array[i] + "] ");
				} else {
					System.out.print(" " + array[i] + " ");
				}
			}
		} else if (decision == 2) {
			for (int i = 0; i < array.length; i++) {
				if (array[i] % 7 == 0) {
					System.out.print(" [" + array[i] + "] ");
				} else {
					System.out.print(" " + array[i] + " ");
				}
			}
		} else {
			System.out.println("Decisión inválida");
		}
		sn.close();

	}

}

