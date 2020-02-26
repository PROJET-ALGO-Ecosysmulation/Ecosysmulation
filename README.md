# Ecosysmulation
import javax.swing.*;
import java.awt.Color;  
import java.awt.event.*;

public class FenetreLac extends JFrame implements ActionListener{
    
    JButton[] lesBoutons;

	
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
        lac.setBounds(50,30,900,400);
        lac.setBackground(Color.cyan);
        monConteneur.add(lac);
        
        //création boutons
        lesBoutons = new JButton[10]; 
        int indice=0;
        for(int i=0;i<5;i++){
            for(int j=0;j<2;j++){
            lesBoutons[indice]=new JButton();
            lesBoutons[indice].setBounds(50+i*120,500+j*120,100,50); 
            lesBoutons[indice].addActionListener(this);
            monConteneur.add(lesBoutons[indice]); 
            }
        }

                
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);             
        setVisible(true);
        
		
	}
    
    public void actionPerformed(ActionEvent e) {
    }
}

