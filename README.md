# Ecosysmulation
import javax.swing.*;
import java.awt.Color;  
import java.awt.event.*;
import  java.awt.Font;

public class FenetreLac extends JFrame implements ActionListener{
    
    JButton[] lesBoutons;
    int a;  // a declarer dans autre programme 
    int temp;
    JButton boutonTemp;
    JLabel temperature;
    JLabel nombreRenards;
    JLabel nombreLoutres;
    JLabel nombreTruites;
    JButton boutonIteration;
    FenetreExplication maFenetreExplication;

	
	public FenetreLac() {
        super("Modélisation du lac");
        setBounds(50,50,1000,800);
        setLayout(null);
        
        JPanel monConteneur = new JPanel();
        monConteneur.setLayout(null);
        monConteneur.setBounds(0,0,1000,800);
        monConteneur.setBackground(Color.lightGray);
        add(monConteneur);
        
        JPanel lac = new JPanel();
        lac.setLayout(null);
        lac.setBounds(50,30,900,500);
        lac.setBackground(Color.lightGray);
        monConteneur.add(lac);
        
        //création boutons
        lesBoutons = new JButton[10]; 
        int indice=0;
        for(int i=1;i<5;i++){
            for(int j=1;j<2;j++){
            lesBoutons[indice]=new JButton();
            lesBoutons[indice].setBounds(100+i*120,550+j*120,100,50); 
            lesBoutons[indice].addActionListener(this);
            monConteneur.add(lesBoutons[indice]); 
            }
        }
        
        //nouvelle créations boutons
        
        boutonTemp = new JButton ("+1 degreC");
        boutonTemp.setBounds (100,550,100,60);
        monConteneur.add (boutonTemp);
        boutonTemp.setBackground(Color.green);
        boutonTemp.addActionListener (this);
        
        boutonIteration = new JButton ("Un An plus Tard");
        boutonIteration.setBounds (220,550,150,60);
        monConteneur.add (boutonIteration);
        
        
        
        
        //ajout images animaux 
        JLabel affRenard = new JLabel(new ImageIcon("./renard.png"));
        affRenard.setBounds(70,80,180,250);
        lac.add(affRenard);
        JLabel affLoutre = new JLabel(new ImageIcon("./loutre.png"));
        affLoutre.setBounds(340,230,250,250);
        lac.add(affLoutre);
        JLabel affTruite = new JLabel(new ImageIcon("./truite.png"));
        affTruite.setBounds(600,200,100,100);
        lac.add(affTruite);
        
        
        //étiquette indiquand le nombre d'animaux
        a=200;
        nombreRenards = new JLabel();
        Font police = new Font(" Arial ",Font.BOLD,20);
		nombreRenards.setFont(police);
        nombreRenards.setText(""+a);
        nombreRenards.setBounds(150,300,50,50);
        lac.add(nombreRenards);
        nombreLoutres = new JLabel();
		nombreLoutres.setFont(police);
        nombreLoutres.setText(""+a);
        nombreLoutres.setBounds(480,420,50,50);
        lac.add(nombreLoutres);
        nombreTruites = new JLabel();
		nombreTruites.setFont(police);
        nombreTruites.setText(""+a);
        nombreTruites.setBounds(630,250,50,50);
        lac.add(nombreTruites);
        
       //Affichage température
        temp = 15;
        temperature = new JLabel();
        Font policeTemp = new Font(" Arial ",Font.BOLD,17);
        temperature.setFont(policeTemp);
        temperature.setText("TEMPERATURE ACTUELLE: " +temp + "degreC");
        temperature.setBounds(50,700,500,100);
        monConteneur.add(temperature);
        
        //Affichage Itérations
        
        
        
         //ajout image lac
        JLabel affLac = new JLabel(new ImageIcon("./lacPhoto.jpg"));
        affLac.setBounds(0,0,900,500);
        lac.add(affLac);
        

        maFenetreExplication = new FenetreExplication();
                
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);             
        setVisible(true);
        
		
	}
    
    public void actionPerformed(ActionEvent e) {
		
		if (e.getSource()== boutonTemp){
			if (temp<45){
				temp +=1;
				temperature.setText("TEMPERATURE ACTUELLE:"+temp + "degreC");
			}
			if (temp>=45){
                JOptionPane.showMessageDialog(this,"Vous avez atteint la temperature maximale");
			}
			maFenetreExplication.setVisible(true);
		    
			
		}
	}
}

