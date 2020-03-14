# Ecosysmulation
	public abstract class EtreVivant {

	protected int dureeVie;
	protected int fecondite;
	protected double coefmort;

	public EtreVivant(int d, int f, double c) {
		dureeVie=d;
	    fecondite=f;
	    coefmort=c;
	}


	public int varTemp(int newtemp, int tempini){

	    int var=Math.abs(newtemp-tempini);
	    return var;
	}


	public double impactTemperature(int temp){

	    if (temp>42) {
	    coefmort -= 0.02*varTemp(temp,42);
	    }

	    if (temp<-15) {
	    coefmort -= 0.02*varTemp(temp,-15);
	    }

	       return coefmort;
	}
	


	public abstract int DeriveGenetique (int a1, int a2, int a3);

	public abstract int SurvieBebe ();

	public abstract int NbAnimauxReproducteurs ();

	public abstract void changeGeneration (int temp);

	public abstract int NbTotalAnimaux ();

	public abstract String toString(int nbIte);

	public abstract String simulGene(int nbIte,int temp);

	//public abstract boolean peutSeDeplacer();
	}
