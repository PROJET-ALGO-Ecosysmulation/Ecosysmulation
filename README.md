# Ecosysmulation
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
        
        // Pour cacher la fenêtre à sa création
        this.setVisible(false);
    }
}
