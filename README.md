# Thiagodeavila


package relogio;

import java.util.Scanner;

public class relogio {
	/* Método  que retorna o angulo considerando que o ponteiro menor move se apenas
	 * na troca de hora. Baseado no fato de que o ponteiro menor move 30 graus por
	 * hora e o ponteiro maior move 6 graus por minuto.*/

	public static int retornaAnguloRelogio(int hora, int minuto) {
		
		int angulo1 = 0, angulo2 = 0, angulo3 = 0;
		angulo1 = hora*30;
		angulo2 = minuto*6;
		angulo3 = angulo1-angulo2;
		
		if (hora > 12) {
			angulo3 = 360 - angulo3;
		}
		return Math.abs(angulo3);
	}
	
/* Método que retorna o angulo considerando que o ponteiro menor move-se a cada minuto.
 * Baseado no fato de que o ponteiro menor move-se 30 graus por hora, o ponteiro maior 
 * move-se 6 graus por minuto e para cada minuto o ponteiro menor move-se 0.5 graus.*/	
public static int retornaAnguloRelogioReal(int hora, int minuto) {
		
		int angulo1 = 0, angulo2 = 0;
		float angulo3 = 0, angulo4;
		angulo1 = hora*30;
		angulo2 = minuto*6;
		angulo3 = (float) (minuto*0.5);
		angulo4 = (angulo1- angulo2 - angulo3);
		
		if (hora > 12) {
			angulo4 = 360 - angulo4;
		}
		return (int)Math.abs(angulo4); // Transforma valores de negativos para positivos
	}

/*Solicita a(s) hora(s) e o(s) minuto(s), verifica se o valor informado é real, imprime
 * o angulo interno e externo através da operação (360 - angulo). */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int hora = 0;
		int minuto = 0;
		Scanner ler = new Scanner(System.in);
		System.out.println("Digite a hora e pressione enter: ");
		hora = ler.nextInt();
		System.out.println("Digite o minuto e pressione enter: ");
		minuto = ler.nextInt();
		if (hora >= 24 || minuto >= 60) {
			System.out.println("Horário inválido.");
		}
		else {
			int angulo = retornaAnguloRelogio(hora, minuto);
			int anguloReal = retornaAnguloRelogioReal(hora, minuto);
			System.out.println("Angulo interno: " + angulo);
			System.out.println("Angulo externo: " + (360-angulo));
			System.out.println("Angulo real interno: " + anguloReal);
			System.out.println("Angulo real externo: " + (360 - anguloReal));
			
		}
	}

}
