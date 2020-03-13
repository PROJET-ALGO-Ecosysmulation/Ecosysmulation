# Ecosysmulation
	public class Animal extends EtreVivant{

	private String nom;
	/*private int Allele1;
	private int Allele2;
	private int Allele3;*/
	private int [] popAnimal;
	private double surv; //pourcentage survie bb


	public Animal (String n,/* int A1, int A2, int A3,*/ int d, int f, double c, double s) {
		super(d,f,c);
		nom=n;
		surv=s;
		//Allele1=A1;
	   // Allele2=A2;
		//Allele3=A3;

		this.popAnimal=new int [d];

	   for(int j=0; j<popAnimal.length; j++){
			double rand =100*Math.random()+10;
			int rand2 = (int)rand;
			popAnimal[j]=rand2;

			}

	}

	public int DeriveGenetique (int a1, int a2, int a3){
	    int sum = 0;
	    while (sum==0){
		int a=(int)Math.random();
		int b=(int)Math.random();
		int c=(int)Math.random();
		sum = a+b+c;
	    }
		return sum;
	}

	public double getmort(){
	    return super.getmort();
	}

	public int getfecondite(){
	    return super.getfecondite();
	}

	public int SurvieBebe (){
		double res = popAnimal[0]*surv;
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

	public void changeGeneration () {

			int a=popAnimal[1];

			popAnimal[1]=SurvieBebe();
			popAnimal[0]=super.getfecondite()*NbAnimauxReproducteurs();

		int b=1;

		for(int h=2; h<popAnimal.length; h++){
		b=popAnimal[h];
		double m= a*getmort();//à tester
		int mo=(int)m;
		popAnimal[h]=mo;//modifier ici pour que tous les renards ne survivent pas
		a=b;
			}

	}


	public int NbTotalAnimaux () {
		int nbtotAn=0;

	for(int j=0; j<popAnimal.length; j++){
		    nbtotAn += popAnimal[j];
	    }

	return nbtotAn;
	}

	public String toString(int nbIte) {
		String res = new String();

		res = "Population annee "+nbIte+" de "+nom+" : ";
		   for(int j=0; j<popAnimal.length; j++){ //affiche tableau à chaque itération
		    res += popAnimal[j];
		    res +="|";
		} 

		return res;
	}
	
	
	public String simulGene(int nbIte){
		String aff = new String ();

		for (int i=0; i<nbIte+1;i++) {
			aff=this.toString(i);
			this.changeGeneration();
			aff+="\n"; // à la ligne?
		}
	return aff;
	}

	}
