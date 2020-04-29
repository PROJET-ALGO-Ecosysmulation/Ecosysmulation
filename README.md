# Ecosysmulation

	public abstract class EtreVivant {

	protected int dureeVie;//Espérance de vie d'une espèce
	protected int fecondite;//Donne combien de petits peut avoir un couple
	protected double coefsurvie;//Chance de survie de survivre l'année suivante

	public EtreVivant(int d, int f, double c) {
		dureeVie=d;
	    fecondite=f;
	    coefsurvie=c;
	}

	public int calculVar(int newval, int valini){//Calcul la variation de pH ou de température  


	    int var=Math.abs(newval-valini);
	    return var;
	}


	public double impactTemperature(int temp){//Modifie le coefsurvie si la température et trop élevée ou trop basse


	    if (temp>30) {
	    coefsurvie -= 0.05*calculVar(temp,45);
	    }

	    if (temp<5) {
	    coefsurvie -= 0.05*calculVar(temp,-15);
	    }

	    return coefsurvie;
	}


	public double impactpH(int valpH){//Modifie le coefsurvie s'il y a une variation de pH


	    if ((valpH>8)||(valpH<6)) {
	    coefsurvie -= 0.05*calculVar(valpH,7);
	    }

	    return coefsurvie;
	}

	public abstract void chasse();

	public abstract void surpeche();

	public abstract int SurvieBebe ();

	public abstract int NbAnimauxReproducteurs ();

	public abstract void changeGeneration (int temp, int pH, Animal animalmange);

	public abstract int NbTotalAnimaux ();

	public abstract void mange (Animal estMange);

	public abstract boolean famine ();

	public abstract void afficheliste();

	public abstract void plafond();

	}
