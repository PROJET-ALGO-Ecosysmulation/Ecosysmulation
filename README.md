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

	public int calculVar(int newval, int valini){

	    int var=Math.abs(newval-valini);
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


	    if (temp>42) {
	    coefmort -= 0.05*calculVar(temp,42);
	    }

	    if (temp<-15) {
	    coefmort -= 0.05*calculVar(temp,-15);
	    }

	    /*if (validationCoefMort(coefmort)){
	    return coefmort;} else{
	    return 0;}*/

	    return Math.abs(coefmort);
	}


	public double impactpH(int valpH){


	    if ((valpH>9)||(valpH<6.5)) {
	    coefmort -= 0.05*calculVar(valpH,7);
	    }

	    return Math.abs(coefmort);
	}
	
	
	public double chasse() {
	    this.coefmort-=0.2;
	   return coefmort;
	}

	public abstract int SurvieBebe ();

	public abstract int NbAnimauxReproducteurs ();

	public abstract void changeGeneration (int temp, int pH,Animal estMange);

	public abstract int NbTotalAnimaux ();

	public abstract String toString(int nbIte);

	public abstract void mange (Animal estMange);

	public abstract boolean famine ();

	public abstract void afficheliste();


	//public abstract String simulGene(int nbIte,int temp);

	//public abstract boolean peutSeDeplacer();
	}
