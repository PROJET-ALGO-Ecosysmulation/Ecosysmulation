import java.util.LinkedList;
	
	/** Cette méthode permet de définir un animal, 
	 * initialiser sa population, pose les principes de base de l'évolution de la population, 
	 * et *il y a quelques méthode permettant d'altérer une population animal 
	 */
	 
	 
public class Animal extends EtreVivant{

	private String nom;
	private int [] popAnimal; // tableau avec le nombre d'animaux selon âge (allant de 0 à durée de vie d'un animal)
	private double surviebb; //pourcentage de bébés qui survivent de l'âge 0 à l'âge 1
	private LinkedList <Integer> listeNbAn;// liste du nombre total d'animaux à chaque génération
	private int generation=0;  //Permet de savoir à quelle génération on est

	public Animal (String n,int d, int f, double c, double s) {
		super(d,f,c);
		nom=n;
		surviebb=s;

		this.popAnimal=new int [d];
		int nb=1;

		switch (nom) {
		case "Aigle":
		nb=6;
		break;

		case "Renard":
		nb=15;
		break;

		case "Loutre":
		nb=15;
		break;

		case "Truite":
		nb=25;
		break;

		case "Insecte":
		nb=100;
		break;
		}

	    popAnimal[1]=nb; // Initialisation de la case des animaux âgés de 1 an à un nombre que nous avons choisi
		this.listeNbAn = new LinkedList <Integer>(); //Initialisation du tableau contenant le nombre total d'animaux de chaque espèce
		listeNbAn.add(nbTotalAnimaux());

	}

	public void afficheliste(){     //Permet d'afficher le nombre total d'individu de chaque espèce pour vérification
    
		for (int i=0; i<listeNbAn.size();i++){
			System.out.print("Population totale "+i+" : "+listeNbAn.get(i));
			System.out.println();
		}
	}

	public int survieBebe (){        //Permet de calculer le nombre de bébés passant à l'âge adulte (1 an)
		double res = popAnimal[0]*surviebb;
		int bbsurvie = (int)res;
		return bbsurvie;
	}

	public int nbAnimauxReproducteurs (){   //Permet de caculer le nombre d'animaux reproducteurs (animaux âgés de plus d'un an (1 an compris))
		int sumAnAd = 0;    //Animaux pouvant s'accoupler

		for(int j=1; j<popAnimal.length; j++){
			sumAnAd += popAnimal[j];
		}
		double conv = sumAnAd*0.5;
		int nbAnRep = (int)conv;
	    return nbAnRep; 
	}

	public void changeGeneration (int temp, int pH, Animal animalmange) {     //Permet de passer à la génération suivante en prenant en compte toutes les méthodes pouvant altérer la population

		generation +=1;
		listeNbAn.add(nbTotalAnimaux());

		int a=popAnimal[1];
		int b=1;

		coefsurvie=super.impactTemperature(temp);
		plafond();      //Permet de ne pas dépasser une valeur seuil (1 000 individus)
	
		if(nom=="Truite"){
			coefsurvie=super.impactpH(pH);
			plafond();
		}

		this.mange(animalmange);
		plafond();

		popAnimal[1]=survieBebe();
		popAnimal[0]=fecondite*nbAnimauxReproducteurs();    //Calcul le nombre de bébés en fonction du nombre d'animaux reproducteurs

		//Application du coefsurvie et gain d'une année de tous les animaux d'un an ou plus
		for(int h=2; h<popAnimal.length; h++){
			b=popAnimal[h];
			double m= a*coefsurvie;
			int mo=(int)m;
			popAnimal[h]=mo;
			a=b;
		}
		plafond();

		for(int i=0; i<popAnimal.length; i++){//Si le nombre d'animal devient négatif, le mettre à 0
			if (popAnimal[i]<0){
				popAnimal[i]=0;
			} 
		}
	
		regulation();
	}

	public void changeGeneration (int temp, int pH) { // changegeneration pour le dernier animal de la chaine alimentaire
		generation +=1;
		listeNbAn.add(nbTotalAnimaux());

		int a=popAnimal[1];
		int b=1;
	
		coefsurvie=super.impactTemperature(temp);
		plafond();

		popAnimal[1]=survieBebe();
		popAnimal[0]=fecondite*nbAnimauxReproducteurs();

		//Application du coefsurvie
		for(int h=2; h<popAnimal.length; h++){
			b=popAnimal[h];
			double m= a*coefsurvie;
			int mo=(int)m;
			popAnimal[h]=mo;
			a=b;
		}
		plafond();

		for(int i=0; i<popAnimal.length; i++){//Si le nombre d'animaux devient négatif, le mettre à 0
			if (popAnimal[i]<0){
				popAnimal[i]=0;
			} 
		}

		regulation();
	}

	public void regulation() {//Défini les coefficients de régulation pour chaque animal

		double mu=0;
		switch (nom) {
		case "Aigle":
		mu=0.02;
		break;

		case "Renard":
		mu=0.0045;
		break;

		case "Loutre":
		mu=0.0045;
		break;

		case "Truite":
		mu=0.9;
		break;

		case "Insecte":
		mu=0;
		break;
		}

		int oldpopulation = nbTotalAnimaux();
		double newpopulation = oldpopulation-mu*Math.pow((oldpopulation),2);   //Application du coefficient de régulation
		int popfinale = (int) newpopulation;
		int differencepop=oldpopulation-popfinale;    //Calcul le nombre d'animaux en trop à enlever

		//Diminue la population en fonction du nombre d'animaux en trop
		for (int i = 1; i<popAnimal.length; i++) {
			if ((popAnimal[i] != 0)&&(differencepop!=0)) {
				popAnimal[i]-=1;
				differencepop-=1;
			}
		}
	}

	public int nbTotalAnimaux () {  //Calcul le nombre total d'individus d'une espèce
		int nbtotAn=0;

		for(int k=0; k<popAnimal.length; k++){
			nbtotAn += popAnimal[k];
		}    
    return nbtotAn;
	}


	public void plafond () {//permet de mettre en place une valeur seuil pour éviter qu'il y ait trop d'animaux

		int oldnbtotAn=nbTotalAnimaux();
		int newnbtotAn=0;

		//Pour limiter la population (plafond)
		if (oldnbtotAn > 1000) {
			newnbtotAn=1000;
			int diffpop= oldnbtotAn-newnbtotAn;

			//Diminue la population initiale
			int j=0;
			while (diffpop!=0) {
				if (j==popAnimal.length) {
					j=0;  
				}
				if (popAnimal[j] != 0) {
					popAnimal[j]-=1;
					diffpop-=1;
				}
				j++;  
			}
		}
	}


	public boolean famine (){ //Vérifie si le nombre d'individus d'une espèce a diminué

		int nbAn=listeNbAn.get(generation-1)-listeNbAn.get(generation);

		if (nbAn > 0){
			return true;
		} else { 
			return false; 
		}
	}



	public void mange (Animal estMange){  //Permet de faire mourir des individus d'une espèce s'il n'y a pas assez à manger
		double coeffamine=0;
		double r =0; //Rapport à la génération 0 entre proies et prédateurs
		double rActuel; //Rapport à la génération actuelle entre proies et prédateurs

		if (famine()==true){
			r=estMange.listeNbAn.get(0)/this.listeNbAn.get(0);    //Calcul du rapport à la génération 0 entre proies et prédateurs
			rActuel=estMange.listeNbAn.get(generation-1)/this.listeNbAn.get(generation-1);    //Cacul du rapport à la génération actuelle entre proies et prédateurs
			if (r/rActuel<1){
				coeffamine=r/rActuel;   //Comparaison des rapports
			}
			coefsurvie -= coeffamine;    //Modification du coefficient de survie en fonction d'un gros manque de nourriture ou non 
		}
		plafond();
	}

	public void chasse() {   //Permet d'introduire la chasse des renards
		this.coefsurvie-=0.2;
		plafond();
	}

	public void surpeche() {//Permet d'introduire la pêche des truites
		this.coefsurvie-=0.5;
		plafond();
	}
}
