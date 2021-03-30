# EjerciciosJava
Algunos ejercicios varios de Java
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
