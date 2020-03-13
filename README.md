# Ecosysmulation
	public class TestRenard {

	public static void main (String[] args) {
		Animal Renard = new Animal("Renard",8,7,0.9,0.2);
	    int nbAnnees=3; //nombre itération
	   // int [] popRenard = {100,21,14,15,17,13,17,14}; //initialisation population de base| à faire générer aléatoirement 

	   for (int i=0; i<nbAnnees+1;i++) {
		System.out.print(Renard.toString(i));
	    Renard.changeGeneration();
	    System.out.println();
		}


	  }
	}

	 /* System.out.println("generation 0");
	    for(int k=0; k<popRenard.length; k++){ //affiche tableau à chaque itération
		System.out.print(popRenard[k]);
		System.out.print("|");
	    } 

	    //double coefmort=0.9;//dépend du paramètre de mort


	    for(int i=0; i<nbAnnees;  i++){

		int sumRenardAd = 0;//Renard pouvant s'accoupler

		for(int j=1; j<popRenard.length; j++){
		    sumRenardAd += popRenard[j];
		}

		int nbCouple = (int)sumRenardAd/2;
		System.out.println("Couple "+nbCouple);
		System.out.println("Renard total adulte "+sumRenardAd);

		int a=1;
		int b=1;
		a=popRenard[1];
		double x = popRenard[0]*0.2;
		System.out.println("Bébés survivants "+x);
		int y=(int) x;
		popRenard[1]=y;
		popRenard[0]=nbCouple*6; //remplacement tableau pour nouvelle génération Z
		for(int h=2; h<popRenard.length; h++){
		    b=popRenard[h];
		    double m= a*Renard.getmort();
		    int mo=(int)m;
		    popRenard[h]=mo;//modifier ici pour que tous les renards ne survivent pas
		    a=b;
		}

		System.out.println("génération "+ (i+1));
		for(int j=0; j<popRenard.length; j++){ //affiche tableau à chaque itération
		    System.out.print(popRenard[j]);
		    System.out.print("|");
		} 
		System.out.println();
		System.out.println();
	    }

	}*/

