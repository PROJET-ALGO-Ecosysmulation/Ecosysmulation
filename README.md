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

	/*public boolean validationCoefMort(double coef){
	    boolean ok=true;
	    if (coef<0) {
	    ok=false;
	    }
	    return ok;
	   } */


	public double impactTemperature(int temp){

	// les limites de températures -15 et 42 ont été fixées au hasard; à choisir plus tard?

	    if (temp>42) {
	    coefmort -= 0.05*varTemp(temp,42);
	    }

	    if (temp<-15) {
	    coefmort -= 0.05*varTemp(temp,-15);
	    }

	    /*if (validationCoefMort(coefmort)){
	    return coefmort;} else{
	    return 0;}*/

	    return Math.abs(coefmort);
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
