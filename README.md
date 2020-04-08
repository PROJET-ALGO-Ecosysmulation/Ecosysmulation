# Ecosysmulation
	import java.util.LinkedList; 

	public class TestRenard {

	public static void main (String[] args) {
	    Animal Aigle;
	    Animal Renard;
	    Animal Loutre;
	    Animal Truite;
	    Animal Insecte;

	    Aigle = new Animal ("Aigle", 25,1,0.9,0.9);
	    Renard = new Animal("Renard",5,7,0.9,0.2);
	    Loutre = new Animal("Loutre",8,2,0.9,0.5);
	    Truite = new Animal("Truite",10,2500,0.9,0.01);
	    Insecte = new Animal(10,2500,0.9,0.01);

		LinkedList<Animal> chaineAlim=new LinkedList<Animal>();
		chaineAlim.add(Aigle);
		chaineAlim.add(Renard);
		chaineAlim.add(Loutre);
		chaineAlim.add(Truite);
		chaineAlim.add(Insecte);  

	    FenetreLac maFenetreLac = new FenetreLac();


		/*Animal ani1 = Renard;
		int i = 1;
	    while(chaineAlim.get(i) != Insecte){


		System.out.print("Population de "+chaineAlim.get(i));

		ani1.mange(chaineAlim.get(i));
		ani1=chaineAlim.get(i);
		i++;
	    }



		for (int i=0; i<nbAnnees+1;i++) {
		System.out.print(Renard.toString(i));
	    Renard.changeGeneration(temp,pH);
	    System.out.println();
		}*/


	  }
	}
