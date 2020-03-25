import javax.swing.*; 
import java.awt.*; 
import java.util.LinkedList;

public class FenetreExplication extends JFrame{

public FenetreExplication(){


    this.setTitle("Explication des paramètres");
    this.setLayout(null);
    this.setSize(600,600);
    this.setLocation(1000,200);

    // Pour empêcher le redimensionnement de la fenêtre
    this.setResizable(false);
    
    JPanel monConteneur = new JPanel();
    monConteneur.setLayout(null);
    monConteneur.setBounds(0,0, getWidth(),getHeight());
    monConteneur.setBackground(Color.lightGray);
       
    
    // Création des JLabel pour afficher les explications
    JLabel[] lesTextes = new JLabel[10]; 
    int indice=0;
    for(int i=0;i<10;i++){
       lesTextes[i]=new JLabel();
       lesTextes[i].setBounds(10,10+i*30,getWidth(),20); 
       monConteneur.add(lesTextes[i]);       
    }
        
    lesTextes[0].setText("Tant que le pH de l'eau est entre 6,5 à 9,0, les populations évoluent normalement");
    lesTextes[1].setText("Pour un pH inferieur a 6,5 ou superieur a 9,0 les organismes peuvent subir un stress qui compromettrait certaines de leurs fonctions vitales");
    lesTextes[2].setText("Pour ces plages de pH extremes on observe donc une mortalites des populations plus importantes");
    lesTextes[3].setText(" ");
    lesTextes[4].setText(" ");
    lesTextes[5].setText(" ");
    lesTextes[6].setText(" ");
    lesTextes[7].setText(" ");   
    
    add(monConteneur);
    
    // Pour cacher la fenêtre à sa création
    this.setVisible(false);
}
}
