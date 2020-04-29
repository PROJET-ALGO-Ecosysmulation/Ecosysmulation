# Ecosysmulation
/** Cette méthode permet de définir un animal, initialiser sa population, pose les principes de base de l'évolution de la population, et *il y a quelques méthode permettant d'altérer une population animal
*/	
	
	import java.util.LinkedList;

	public class Animal extends EtreVivant{

	private String nom;
	private int [] popAnimal; // Tableau avec nb d'animaux selon âge (allant de 0 à durée de vie d'un animal)
	private double surviebb; //Pourcentage de bébés qui survivent de l'âge 0 à l'âge 1
	private LinkedList <Integer> listeNbAn;// Liste du nombre total d'animaux à chaque génération
	private int generation=0; //Permet de savoir à quelle génération on est
	//private final static String POPFIN = "Insecte" ;


	public Animal (String n,int d, int f, double c, double s) { 
		super(d,f,c);
		nom=n;
		surviebb=s;

	    this.popAnimal=new int [d];

	/*int multip=1;
	int add=1;
	int nb=1;

	switch (nom) {
	    case "Aigle":
		multip=1;
		add=1;
		nb=5;
		break;

	    case "Renard":
		multip=6;
		add=6;
		nb=12;
		break;

	    case "Loutre":
		multip=4;
		add=6;
		nb=12;
		break;

	    case "Truite":
		multip=4;
		add=10;
		nb=25;
		break;

	    case "Insecte":
		multip=8;
		add=6;
		nb=100;
		break;


	}*/

	    for(int j=0; j<popAnimal.length; j++){ //Initialisation du tableau à zéro
			popAnimal[j]=0;
	    }
	    popAnimal[1]=nb; //On initialize la case des animaux âgés de 1 an à un nombre que nous avons choisi


	    /*for(int j=0; j<popAnimal.length; j++){
			double rand =multip*Math.random()+add;
			int rand2 = (int)rand;
			popAnimal[j]=rand2;
			}*/



	    this.listeNbAn = new LinkedList <Integer>(); //Initialisation du tableau contenant le nombre total d'animaux de chaque espèce
	    listeNbAn.add(NbTotalAnimaux());

	}

	/*public Animal (int d, int f, double c, double s) {
	    this(Animal.POPFIN,d,f,c,s);

	}*/

	public void afficheliste(){ //Permet d'afficher le nombre total d'individu de chaque espèce
	    for (int i=0; i<listeNbAn.size();i++){
		System.out.print("Population totale "+i+" : "+listeNbAn.get(i));
		System.out.println();

	    }
	}

	//permet de calculer le nombre de bébés passant à l'âge adulte (1 an)
	public int SurvieBebe (){ 
		double res = popAnimal[0]*surviebb;
		int bbsurvie = (int)res;

	return bbsurvie;
	}

	public int NbAnimauxReproducteurs (){ //Permet de caculer le nombre d'animaux reproducteurs (animaux âgés de plus d'un an (1 an compris))
		int sumAnAd = 0; //Animaux pouvant s'accoupler

	    for(int j=1; j<popAnimal.length; j++){
		    sumAnAd += popAnimal[j];
	    }

	    double conv = sumAnAd*0.5;
	    int nbAnRep = (int)conv; //Coef à modifier en fonction du pourcentage de femelles

	    return nbAnRep; 
	}

	public void changeGeneration (int temp, int pH, Animal animalmange) { //Permet de passer à la géération suivante en prenant en 											compte toutes les méthodes pouvant altérer la population

	    generation +=1;
	    listeNbAn.add(NbTotalAnimaux());

	    int a=popAnimal[1];
		int b=1;

		coefsurvie=super.impactTemperature(temp);
		plafond(); //Permet de ne pas dépasser une valeur seuil (1 000 individus) 
		coefsurvie=super.impactpH(pH);
		plafond();
		this.mange(animalmange);
		plafond();

	    popAnimal[1]=SurvieBebe();
	    popAnimal[0]=fecondite*NbAnimauxReproducteurs(); //Calcul le nombre de bébés en fonction de nombre d'animaux reproducteurs

	    //Application du coefsurvie et gai d'une année de tous les animaux d'un an ou plus
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

	    regulation(); //Permet de réguler la population pour qu'il n'y ait pas trop d'individu
	}

	public void changeGeneration (int temp, int pH) { // changeGeneration pour le dernier animal de la chaine alimentaire
	    generation +=1;
	    listeNbAn.add(NbTotalAnimaux());

	    int a=popAnimal[1];
	    int b=1;

		coefsurvie=super.impactTemperature(temp);
		plafond();
		coefsurvie=super.impactpH(pH);
		plafond();

	    popAnimal[1]=SurvieBebe();
	    popAnimal[0]=fecondite*NbAnimauxReproducteurs();

	    //Application du coefsurvie
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

	public void regulation() { //Défini les coefficients de régulation pour chaque animal

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
		mu=Math.pow(10,-9);
		break;

	    case "Insecte":
		mu=0;
		break;
	    }



	int oldpopulation = NbTotalAnimaux();
	double newpopulation = oldpopulation-mu*Math.pow((oldpopulation),2); //Application du coefficient de régulation
	int popfinale = (int) newpopulation;
	int differencepop=oldpopulation-popfinale; //Calcul le nombre d'animaux en trop 
	
	    //Diminue la population en fonction du nombre d'animaux en trop
	    for (int i = 1; i<popAnimal.length; i++) {

		if ((popAnimal[i] != 0)&&(differencepop!=0)) {
		    popAnimal[i]-=1;
		    differencepop-=1;
		}

	    }

	}


	public int NbTotalAnimaux () { //Calcul le nombre total d'individus d'une espèce
		int nbtotAn=0;

	    for(int k=0; k<popAnimal.length; k++){
		    nbtotAn += popAnimal[k];
	    }    

	    return nbtotAn;
	}


	public void plafond () { //permet de mettre en place une valeur seuil pour éviter qu'il y ait trop d'animaux

	int oldnbtotAn=NbTotalAnimaux();
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


	public boolean famine (){ //Vérifie si le nombre d'individu d'une espèce à diminué
	    int nbAn=listeNbAn.get(generation-1)-listeNbAn.get(generation);

	    if (nbAn > 0){
		return true;
	    } else { 
	    	return false; 
	    }
	}



	public void mange (Animal estMange){ //Permet de faire mourrir des individus d'une espèce s'il n'y a pas assez à manger
	    double coeffamine=0;
	    double r =0; //Rapport à la génération 0 entre proies et prédateurs
	    double rActuel; //Rapport à la génération actuelle entre proies et prédateurs

	    if (famine()==true){
		r=estMange.listeNbAn.get(0)/this.listeNbAn.get(0);  //Cacul du rapport à la génération 0 entre proies et prédateurs
		rActuel=estMange.listeNbAn.get(generation-1)/this.listeNbAn.get(generation-1); //Cacul du rapport à la génération 													actuelle entre proies et prédateurs
		coeffamine=r/rActuel; //Comparaison des rapports
		coefsurvie -= coeffamine; //Modification du coefficient de survie en fonction de s'il y a beaucoup de manque de 						    nourriture ou pas
	    }
	    plafond();
	}

	public void chasse() { //Permet d'introduire la chasse des renards

	    if (this.nom == "Renard") {
	    this.coefsurvie-=0.2;}
	plafond();

	}

	public void surpeche() { //Permet d'introduire la pêche des truites

	    if (this.nom == "Truite") {
	    this.coefsurvie-=0.2;}
	plafond();

	}


	/*public String toString(int nbIte) {
		String res = new String();

		res = "coefsurvie = "+coefsurvie+ "Population annee "+nbIte+" de "+nom+" : ";
		   for(int j=0; j<popAnimal.length; j++){ //affiche tableau à chaque itération
		    res += popAnimal[j];
		    res +="|";
		} 

		return res;
	}
	*/



	}
