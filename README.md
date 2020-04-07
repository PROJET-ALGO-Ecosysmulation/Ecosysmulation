import javax.swing.*; 
import java.awt.*; 
import java.util.LinkedList;
import java.awt.event.*;



public class FenetreExplication extends JFrame implements ActionListener{
	
		JLabel[] lesTextes;
		JButton reponse;

	public FenetreExplication(){

		this.setTitle("Explication des parametres");
		this.setLayout(null);
		this.setSize(600,600);
		this.setLocation(1000,200);
		reponse = new JButton();
        reponse.setBounds(300,500,120,50);
        reponse.setText("J'ai compris"); 
        reponse.addActionListener(this);
        add(reponse); 
	
 

		// Pour empêcher le redimensionnement de la fenêtre
		this.setResizable(false);
    
		// Pour cacher la fenêtre à sa création
		this.setVisible(false);
	}
	
    public void affBouton1 (){
		
		lesTextes = new JLabel[10]; 
		int indice=0;
		for(int i=0;i<10;i++){
			lesTextes[i]=new JLabel();
			lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
			add(lesTextes[i]);       
		}
		
		lesTextes[0].setText("L'augmentation de la temperature entraine: ");
		lesTextes[1].setText("               - La baisse du niveau des lacs: l'approvisionnement est plus restreint");
		lesTextes[2].setText("               - L'envahissement de certaines especes: dereglement de l'ecosysteme");
		lesTextes[3].setText("               - Developpement des algues: manque d'oxygene pour les especes marines ");
		lesTextes[4].setText(" ");
		lesTextes[5].setText("Les lacs les plus touches : Lac Fracksjon (Suede) :  1,35°C");					 
		lesTextes[6].setText("Lac Superieur (Canada, Etats-­Unis) : 1,16 °C ; ");
		lesTextes[7].setText("Reservoir Kangaroo Creek (Australie) : 1,14 °C ");   
	
		
	}
	
	public void affBouton2 (){
		
		lesTextes = new JLabel[10]; 
		int indice=0;
		for(int i=0;i<10;i++){
			lesTextes[i]=new JLabel();
			lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
			add(lesTextes[i]);       
		}
		
		lesTextes[0].setText("La diminution de la temperature n'est pas un phenomene realiste: ");
		lesTextes[1].setText("Les rapports actuels envisagent plutot une augmentation de la temperature des lacs proportionnellement a");
		lesTextes[2].setText("l'augmentation de la temperature de l'air.");
	
		
	}
	
	public void affBouton3 (){
		
		lesTextes = new JLabel[10]; 
		int indice=0;
		for(int i=0;i<10;i++){
			lesTextes[i]=new JLabel();
			lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
			add(lesTextes[i]);       
		}
		
		lesTextes[0].setText("Tant que le pH de l'eau est entre 6,5 à 9,0, les populations evoluent normalement ");
		lesTextes[1].setText("L'augmentation du pH de l'eau est du : ");
		lesTextes[2].setText("            -Aux fondants sur les routes l'hiver");
		lesTextes[3].setText("            -L'agriculture");
	    lesTextes[4].setText("            -Le beton des infrastructures qui se desagrege sous la pluie...");
		lesTextes[5].setText("Les conséquences en sont:  ");
		lesTextes[6].setText("            -La corrosion des tuyaux d'aqueducs, liberants des molecules toxiques dans les lacs");					 
		lesTextes[7].setText("            -Les fertilisants agricoles se transforment plus facilement en ammoniac ");
		lesTextes[8].setText("            -Les sels deplacent les nutriments des sols, qui faciliterait la prolifération des algues");
		lesTextes[9].setText("             et donc la baisse d'oxygene dans le lac");
		
	}
	
	public void affBouton4 (){
		
		lesTextes = new JLabel[10]; 
		int indice=0;
		for(int i=0;i<10;i++){
			lesTextes[i]=new JLabel();
			lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
			add(lesTextes[i]);       
		}
		lesTestes[0].setText("Tant que le pH de l'eau est entre 6,5 à 9,0, les populations évoluent normalement");
		lesTextes[1].setText("La diminution du pH de l'eau est du : ");
		lesTextes[2].setText("à l'acceleration du controle de la pollution pour contrer les pluies acides");
		lesTextes[3].setText("Les deux tiers des cours d'eau aux Etats-Unis ont connu une alcanisation au début des annees 60.");
		
	}
	
	public void actionPerformed (ActionEvent e){
		
		Object source = e.getSource();
		
		if (source == reponse){
			
			for(int i=0;i<10;i++){
			lesTextes[i].setText("");
			}
		}
	}
		
}
