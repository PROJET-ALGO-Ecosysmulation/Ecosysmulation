# Ecosysmulation
	public abstract class EtreVivant {

	private int dureeVie;
	private int fecondite;
	private double coefmort;

	public EtreVivant(int d, int f, double c) {
		dureeVie=d;
	    fecondite=f;
	    coefmort=c;
	}

	public double getmort(){
	    return coefmort;
	}

	public int getfecondite(){
	    return fecondite;
	}

	public abstract int DeriveGenetique (int a1, int a2, int a3);

	public abstract int SurvieBebe ();

	public abstract int NbAnimauxReproducteurs ();

	public abstract void changeGeneration ();

	public abstract int NbTotalAnimaux ();

	public abstract String toString(int nbIte);

	//public abstract boolean peutSeDeplacer();
	}
