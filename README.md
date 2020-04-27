// ce code permet d'afficher une fenetre qui explique le fonctionnement de notre simulation avant que l'utilisateur ne commence à l'utiliser

import javax.swing.*; 
import java.awt.*; 
import java.util.LinkedList; 
import java.awt.event.*;

public class FenetreRegles extends JFrame implements ActionListener{

JButton b1; // pour pouvoir fermer la fenêtre

	public FenetreRegles(){
		
		this.setTitle("                                                                Comment fonctionne notre simulation ?");
		this.setLayout(null);
		this.setSize(850,400);
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
		lesTextes[1].setText("Notre simulation comporte cinq populations d'animaux :");
		lesTextes[2].setText("Nous avons des renards, des aigles, des loutres, des truites ainsi que des insectes (représentés ici par des sauterelles)");
		lesTextes[3].setText("En changeant un paramètre vous pourrez vous rendre compte de son impact sur l'evolution des populations");
		lesTextes[4].setText("Vous pouvez modifier la température, le pH de l'eau ou interdire ou non la pêche ou la chasse");  
		lesTextes[5].setText("Si vous souhaitez voir l'evolution des populations lorsqu'il n'y a pas de changement vous pouvez cliquer sur un an plus tard");
		lesTextes[6].setText(" ");
		lesTextes[7].setText(" ");
		lesTextes[8].setText(" ");  
				 
		// bouton pour fermer la fenetre
		b1= new JButton("Ok j ai lu les consignes");
		b1.setBounds(getWidth()/2-300/2,getHeight()-200,300,50); 
		b1.addActionListener(this);
		monConteneur.add(b1);
		
		add(monConteneur);
		this.setVisible(true);


	}

	public void actionPerformed(ActionEvent e) {
		Object source = e.getSource();
		this.setVisible(false);
	}	
	
}
