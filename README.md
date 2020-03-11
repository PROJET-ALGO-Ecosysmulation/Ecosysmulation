# Ecosysmulation
public class Animal extends EtreVivant{
	
    private String nom;
    /*private int Allele1;
    private int Allele2;
    private int Allele3;*/
    
	public Animal (String n,/* int A1, int A2, int A3,*/ int d, int f, double c) {
		super(d,f,c);
        nom=n;
        //Allele1=A1;
       // Allele2=A2;
        //Allele3=A3;
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
    
    public double getc(){
        return getmort();
    }
}
