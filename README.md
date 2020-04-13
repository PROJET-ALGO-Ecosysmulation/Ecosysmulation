# Ecosysmulation
	
	public abstract class EtreVivant {

	protected int dureeVie;
	protected int fecondite;
	protected double coefsurvie;

	public EtreVivant(int d, int f, double c) {
		dureeVie=d;
	    fecondite=f;
	    coefsurvie=c;
	}

	public int calculVar(int newval, int valini){

	    int var=Math.abs(newval-valini);
	    return var;
	}


	public double impactTemperature(int temp){


	    if (temp>30) {
	    coefsurvie -= 0.05*calculVar(temp,42);
	    }

	    if (temp<-5) {
	    coefsurvie -= 0.05*calculVar(temp,-15);
	    }

	    /*if (validationcoefsurvie(coefsurvie)){
	    return coefsurvie;} else{
	    return 0;}*/

	    return Math.abs(coefsurvie);
	}


	public double impactpH(int valpH){


	    if ((valpH>8)||(valpH<6)) {
	    coefsurvie -= 0.05*calculVar(valpH,7);
	    }

	    return Math.abs(coefsurvie);
	}

	public double chasse() {

	    this.coefsurvie-=0.2;

	   return coefsurvie;
	}




	public abstract int SurvieBebe ();

	public abstract int NbAnimauxReproducteurs ();

	public abstract void changeGeneration (int temp, int pH, Animal animalmange);

	public abstract int NbTotalAnimaux ();

	public abstract String toString(int nbIte);

	public abstract void mange (Animal estMange);

	public abstract boolean famine ();

	public abstract void afficheliste();
	
	public abstract void chasse();

	public abstract void surpeche();

	}
