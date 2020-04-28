import javax.swing.*;
import java.awt.*; 
import java.util.LinkedList; 
import java.awt.event.*;

public class FenetreExplication extends JFrame implements ActionListener{

JLabel[] lesTextes;
JButton reponse;

public FenetreExplication(){

	this.setTitle("                                                          Explication des parametres");
	this.setLayout(null);
	this.setSize(780,600);
	this.setLocation(1100,200);
	reponse = new JButton();
	reponse.setBounds(300,500,120,50);
	reponse.setText("J'ai compris"); 
	reponse.addActionListener(this);
	add(reponse); 

	// Pour empêcher le redimensionnement de la fenêtre
	this.setResizable(false);

	// Pour cacher la fenêtre à sa création
	this.setVisible(false);
	
	
	//instantiation et placement des JLabbel afin de pouvoir écrire les explications par la suite
	lesTextes = new JLabel[10]; 
	int indice=0;
	for(int i=0;i<10;i++){
		lesTextes[i]=new JLabel();
		lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
		add(lesTextes[i]);       
	}
	
	
}

public void affBouton1 (){
	
	lesTextes[0].setText("L'augmentation de la temperature entraine : ");
	lesTextes[1].setText("               - La baisse du niveau des lacs : l'approvisionnement en eau est plus restreint et pour les lacs de plus petite taille cela peut  ");
	lesTextes[2].setText("                 aller jusqu'a leur disparition");
	lesTextes[3].setText("               - L'envahissement de certaines especes : dereglement de l'ecosysteme");
	lesTextes[4].setText("               - Le developpement des algues qui entraine un manque d'oxygene pour les especes marines ");
	lesTextes[5].setText(" ");
	lesTextes[6].setText("Les lacs les plus touches : Lac Fracksjon (Suede) :  1,35 degré C");					 
	lesTextes[7].setText("Lac Superieur (Canada, Etats-­Unis) : 1,16 degré C  ");
	lesTextes[8].setText("Reservoir Kangaroo Creek (Australie) : 1,14 degré C ");   
	lesTextes[9].setText("");  

	
}

public void affBouton2 (){
	
	lesTextes[0].setText("La diminution de la temperature n'est pas un phenomene realiste : ");
	lesTextes[1].setText("Les rapports actuels envisagent plutot une augmentation de la temperature des lacs ");
	lesTextes[2].setText("proportionnellement a l'augmentation de la temperature de l'air.");
	lesTextes[3].setText("");
	lesTextes[4].setText("");
	lesTextes[5].setText("");
	lesTextes[6].setText("");
	lesTextes[7].setText("");   
	lesTextes[8].setText("");  
	lesTextes[9].setText("");
	
}

public void affBouton3 (){
			
	lesTextes[0].setText("Tant que le pH de l'eau est entre 6,0 et 8,0, les populations evoluent normalement ");
	lesTextes[1].setText("L'augmentation du pH de l'eau est du : ");
	lesTextes[2].setText("            -Aux fondants sur les routes l'hiver");
	lesTextes[3].setText("            -L'agriculture");
	lesTextes[4].setText("            -Le beton des infrastructures qui se desagrege sous la pluie...");
	lesTextes[5].setText("Les consequences en sont:  ");
	lesTextes[6].setText("            -La corrosion des tuyaux d'aqueducs, liberants des molecules toxiques dans les lacs");					 
	lesTextes[7].setText("            -Les fertilisants agricoles se transforment plus facilement en ammoniac ");
	lesTextes[8].setText("");
			
}

public void affBouton4 (){
			
	lesTextes[0].setText("Tant que le pH de l'eau est entre 6,0 et 8,0, les populations évoluent normalement");
	lesTextes[1].setText("La diminution du pH de l'eau est du : ");
	lesTextes[2].setText("        -A l'acceleration du controle de la pollution pour contrer les pluies acides");
	lesTextes[3].setText("        -Les deux tiers des cours d'eau aux Etats-Unis ont connu une alcanisation au début des annees 60.");
	lesTextes[4].setText("");
	lesTextes[5].setText("");
	lesTextes[6].setText("");
	lesTextes[7].setText("");
	lesTextes[8].setText("");
	lesTextes[9].setText("");
	
}

public void affBouton5 (){
	
	lesTextes[0].setText("La peche dans les lacs marque aujourd'hui l'ecosysteme.");
	lesTextes[1].setText("        -Les pecheurs sont de mieux en mieux equipes (Sonar ultra precis, meilleur materiel de peche...");
	lesTextes[2].setText("        -Des guides proposent maintenant leur service pour amener leurs clients vers les zones les plus proliferantes");
	lesTextes[3].setText("        -Des meilleures techniques de peche comme la peche à la jig garantissent de pecher ");
	lesTextes[4].setText("");
	lesTextes[5].setText("Certaines restrictions sont tout de meme mises en place afin de limiter l'impact");
	lesTextes[6].setText("         -L'interdiction de la peche pendant les periodes de proliferations");
	lesTextes[7].setText("         -Des quotas sont instaures par pecheur");
	lesTextes[8].setText("");
	lesTextes[9].setText("Dans tous les cas, responsabilisons-nous et limitons notre peche");
	
}

public void affBouton6 (){
	
	lesTextes[0].setText("Les petits gibiers (cailles, perdrix..) voient leur population diminuer a cause du trafic routier, de l'utilisations de pesticides...");
	lesTextes[1].setText("	La chasse intervient comme element determinant lorsque la population est deja fragilisee");
	lesTextes[2].setText("les petits predateurs (renard roux, fuine, putois..) sont consideres comme des concurrents genants");        
	lesTextes[3].setText("	Ils sont classes nuisibles, et sont donc chasses toute l'annee. Cela conduit a une disparition volontaire des petits predateurs");
	lesTextes[4].setText("");
	lesTextes[5].setText("	Quant au renard, il est un acteur indispensable de la chaine alimentaire:");
	lesTextes[6].setText("Il contribue a l'assainissement des populations des autres especes et a la conservation de leur qualite genetique.");
	lesTextes[7].setText("  Il est un fleau pour les chasseurs et les eleveurs:");
	lesTextes[8].setText("Il se nourrit des rongeurs et detruit donc les culture, il s'en prend aux animaux laches dans la nature par les chasseurs  ");
	lesTextes[9].setText("	Les chasseurs tuent toute l'annee ce predateur, en agissant ainsi, ils amplifient la propagation des maladies");
	
}

public void supprimerText (){
	for(int i=0;i<10;i++){
		lesTextes[i].setText("");
	}
}

// pour supprimer la fenetre d'explication lorsque l'utilisateur l'a lu et a cliqué sur "J'ai compris"
public void actionPerformed (ActionEvent e){

	Object source = e.getSource();
	
	if (source == reponse){
		
		for(int i=0;i<10;i++){
		lesTextes[i].setText("");
		this.setVisible(false);
		}
	}
}
}
