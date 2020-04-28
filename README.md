# Ecosysmulation
	import java.util.LinkedList;

	public class Animal extends EtreVivant{

	private String nom;
	private int [] popAnimal; // tableau avec nb d'animaux selon âge (allant de 0 à durée de vie d'un animal)
	private double surviebb; //pourcentage de bébés qui survivent de l'âge 0 à l'âge 1
	private LinkedList <Integer> listeNbAn;// liste du nombre total d'animaux à chaque génération
	private int generation=0;
	//private final static String POPFIN = "Insecte" ;


	public Animal (String n,int d, int f, double c, double s) {
		super(d,f,c);
		nom=n;
		surviebb=s;

	    this.popAnimal=new int [d];

	int multip=1;
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


	}

	    for(int j=0; j<popAnimal.length; j++){
			popAnimal[j]=0;
	    }
	    popAnimal[1]=nb;


	    /*for(int j=0; j<popAnimal.length; j++){
			double rand =multip*Math.random()+add;
			int rand2 = (int)rand;
			popAnimal[j]=rand2;
			}*/



	    this.listeNbAn = new LinkedList <Integer>();
	    listeNbAn.add(NbTotalAnimaux());

	}

	/*public Animal (int d, int f, double c, double s) {
	    this(Animal.POPFIN,d,f,c,s);

	}*/

	public void afficheliste(){
	    for (int i=0; i<listeNbAn.size();i++){
		System.out.print("Population totale "+i+" : "+listeNbAn.get(i));
		System.out.println();

	    }
	}


	public int SurvieBebe (){
		double res = popAnimal[0]*surviebb;
		int bbsurvie = (int)res;

	return bbsurvie;
	}

	public int NbAnimauxReproducteurs (){
		int sumAnAd = 0;//Animaux pouvant s'accoupler

	    for(int j=1; j<popAnimal.length; j++){
		    sumAnAd += popAnimal[j];
	    }

	    double conv = sumAnAd*0.5;
	    int nbAnRep = (int)conv; //coef à modifier en fonction du pourcentage de femelles

	    return nbAnRep; 
	}

	public void changeGeneration (int temp, int pH, Animal animalmange) {

	    generation +=1;
	    listeNbAn.add(NbTotalAnimaux());

	    int a=popAnimal[1];
		int b=1;

		coefsurvie=super.impactTemperature(temp);
		plafond();
		coefsurvie=super.impactpH(pH);
		plafond();
		this.mange(animalmange);
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

	public void changeGeneration (int temp, int pH) { // changegeneration pour le dernier animal de la chaine alimentaire
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

	public void regulation() {

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
	double newpopulation = oldpopulation-mu*Math.pow((oldpopulation),2);
	int popfinale = (int) newpopulation;
	int differencepop=oldpopulation-popfinale;

	    //Diminuer la population
	    for (int i = 1; i<popAnimal.length; i++) {

		if ((popAnimal[i] != 0)&&(differencepop!=0)) {
		    popAnimal[i]-=1;
		    differencepop-=1;
		}

	    }

	}


	public int NbTotalAnimaux () {
		int nbtotAn=0;

	    for(int k=0; k<popAnimal.length; k++){
		    nbtotAn += popAnimal[k];
	    }    

	    return nbtotAn;
	}


	public void plafond () {

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


	public boolean famine (){

	    int nbAn=listeNbAn.get(generation-1)-listeNbAn.get(generation);

	    if (nbAn > 0){
		return true;
	    } else { return false; }

	}



	public void mange (Animal estMange){
	    double coeffamine=0;
	    double r =0;
	    double rActuel;

	    if (famine()==true){
		r=estMange.listeNbAn.get(0)/this.listeNbAn.get(0);
		rActuel=estMange.listeNbAn.get(generation-1)/this.listeNbAn.get(generation-1);
		coeffamine=r/rActuel;
		coefsurvie -= coeffamine;
	    }
	    plafond();
	}

	public void chasse() {

	    if (this.nom == "Renard") {
	    this.coefsurvie-=0.2;}
	plafond();

	}

	public void surpeche() {

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
