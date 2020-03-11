# Ecosysmulation
public abstract class EtreVivant {
	
    public int dureeVie;
    public int fecondite;
    public double coefmort;
    
	public EtreVivant(int d, int f, double c) {
		dureeVie=d;
        fecondite=f;
        coefmort=c;
    }
    
    public double getmort(){
        return coefmort;
    }

    
    //public abstract boolean peutSeDeplacer();
}

