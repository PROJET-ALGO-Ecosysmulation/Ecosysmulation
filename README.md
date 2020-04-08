# Ecosysmulation
	import java.util.LinkedList;

	public class Animal extends EtreVivant{

	private String nom;
	private int [] popAnimal;
	private double surviebb; //pourcentage survie bb
	private LinkedList <Integer> listeNbAn;
	private int generation=0;
	private final static String POPFIN = "Insecte" ;

	// Ecrire methode SurvieAnimaux avec méthode mere temperature + changer changement generation après impact temp

	public Animal (String n,/* int A1, int A2, int A3,*/ int d, int f, double c, double s) {
		super(d,f,c);
		nom=n;
		surviebb=s;

	    this.popAnimal=new int [d];

	   for(int j=0; j<popAnimal.length; j++){
			double rand =10*Math.random()+10;
			int rand2 = (int)rand;
			popAnimal[j]=rand2;

			}


	    this.listeNbAn = new LinkedList <Integer>();
	    listeNbAn.add(NbTotalAnimaux());


	}

	public Animal (int d, int f, double c, double s) {
	    this(Animal.POPFIN,d,f,c,s);

	}

	public void afficheliste(){
	    for (int i=0; i<listeNbAn.size();i++){
		System.out.print("Population totale "+i+" : "+listeNbAn.get(i));
		System.out.println();

	    }
	}


	public int SurvieBebe (){
		double res = popAnimal[0]*surviebb*coefsurvie;// coefsurvie à mettre ou pas? comment bb peuvent être impactés aussi par paramètres ?
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

		/*if (animalmange.nom == Animal.POPFIN){
		    coefsurvie=animalmange.impactTemperature(temp);
		    coefsurvie=animalmange.impactpH(pH);
		}

		if (this.nom == "Renard") {
		    super.chasse();
		}*/
		for(int i=0; i<popAnimal.length; i++){
		    if (popAnimal[i]<0){
		    popAnimal[i]=0;
		    } 
		}

		coefsurvie=super.impactTemperature(temp);
		coefsurvie=super.impactpH(pH);
		//this.mange(animalmange);

			popAnimal[1]=SurvieBebe();
			popAnimal[0]=fecondite*NbAnimauxReproducteurs();


		for(int h=2; h<popAnimal.length; h++){
		b=popAnimal[h];
		double m= a*coefsurvie;
		int mo=(int)m;
		popAnimal[h]=mo;//modifier ici pour que tous les renards ne survivent pas
		a=b;
			}

		for(int i=0; i<popAnimal.length; i++){
		    if (popAnimal[i]<0){
		    popAnimal[i]=0;
		    } 
		}


	}

	public void changeGeneration (int temp, int pH) { // changegeneration pour le dernier animal de la chaine alimentaire
	    generation +=1;
	    listeNbAn.add(NbTotalAnimaux());

	    int a=popAnimal[1];
	    int b=1;

	    for(int i=0; i<popAnimal.length; i++){
		    if (popAnimal[i]<0){
		    popAnimal[i]=0;
		    } 
		}

		coefsurvie=super.impactTemperature(temp);
		coefsurvie=super.impactpH(pH);

			popAnimal[1]=SurvieBebe();
			popAnimal[0]=fecondite*NbAnimauxReproducteurs();


		for(int h=2; h<popAnimal.length; h++){
		b=popAnimal[h];
		double m= a*coefsurvie;
		int mo=(int)m;
		popAnimal[h]=mo;//modifier ici pour que tous les renards ne survivent pas
		a=b;
			}

		for(int i=0; i<popAnimal.length; i++){
		    if (popAnimal[i]<0){
		    popAnimal[i]=0;
		    } 
		}

	}



	public int NbTotalAnimaux () {
		int nbtotAn=0;

	for(int j=0; j<popAnimal.length; j++){
		    nbtotAn += popAnimal[j];
	    }

	return nbtotAn;
	}


	public boolean famine (){

	    int nbAn=listeNbAn.get(generation)-listeNbAn.get(generation+1);

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
		rActuel=estMange.listeNbAn.get(generation)/this.listeNbAn.get(generation);
		coeffamine=r/rActuel;
		coefsurvie -= coeffamine;
	    }

	}


	public String toString(int nbIte) {
		String res = new String();

		res = "coefsurvie = "+coefsurvie+ "Population annee "+nbIte+" de "+nom+" : ";
		   for(int j=0; j<popAnimal.length; j++){ //affiche tableau à chaque itération
		    res += popAnimal[j];
		    res +="|";
		} 

		return res;
	}



	}
