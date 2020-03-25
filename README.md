import javax.swing.*; 
import java.awt.*; 
import java.util.LinkedList;

public class FenetreRegles extends JFrame{

	public FenetreRegles(){


		this.setTitle("                                                                Comment fonctionne notre simulation ?");
		this.setLayout(null);
		this.setSize(850,600);
		this.setLocation(1050,50);
		this.setResizable(false);
		
		JPanel monConteneur = new JPanel();
		monConteneur.setLayout(null);
		monConteneur.setBounds(0,0, getWidth(),getHeight());
		monConteneur.setBackground(Color.lightGray);
	   
	   
		JLabel[] lesTextes = new JLabel[10]; 
		int indice=0;
		for(int i=0;i<10;i++){
		   lesTextes[i]=new JLabel();
		   lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
		   monConteneur.add(lesTextes[i]);       
		}
			
		lesTextes[0].setText("Bienvenue dans Ecosymulation qui vous permet de simuler l'evolution d'un ecosysteme");
		lesTextes[1].setText("Notre simulation comporte trois populations d'animaux : une population de renards, une de loutres et une de truites");
		lesTextes[2].setText("En changeant un paramètre, tels que le pH ou la température, vous pourrez vous rendre compte de son impact sur l'evolution des populations");
		lesTextes[3].setText("Si vous souhaitez voir l'evolution des populations lorsqu'il n'y a pas de changement vous pouvez cliquer sur + 1 an");
		lesTextes[4].setText(" ");
		lesTextes[5].setText(" ");
		lesTextes[6].setText(" ");
		lesTextes[7].setText(" ");   
		
		add(monConteneur);
		this.setVisible(true);
    
    
	}
}
