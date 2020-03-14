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


	public double impactTemperature(int temp){

		if (((temp > 40)&&(temp < 45)) || ((temp > -25)&&(temp < -13))){
			coefmort=0.25; //25% survivent l'année suivante
		}

		if ((temp >= 45)||(temp <= -25)) {
			coefmort=0; //0% survivent l'année suivante
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
