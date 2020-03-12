# Ecosysmulation
public class Animal extends EtreVivant{

	private String nom;
	/*private int Allele1;
	private int Allele2;
	private int Allele3;*/
	private int [] popAnimal;


	public Animal (String n,/* int A1, int A2, int A3,*/ int d, int f, double c) {
		super(d,f,c);
		nom=n;
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

	public int SurvieBebe (){
		double res = popAnimal[0]*0.2;
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
	
	//popAnimal[0]=super.getfecondite()*NbAnimauxReproducteurs();//à tester
	
	        int a=popAnimal[1];
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
	
	}
