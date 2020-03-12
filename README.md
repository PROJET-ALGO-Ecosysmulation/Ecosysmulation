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
    
    //public abstract boolean peutSeDeplacer();
}

