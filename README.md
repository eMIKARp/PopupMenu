# PopupMenu
a piece of code that shows popup menu after clicking right mouse button on frame area


    package menukontekstowe;
    
    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;

    public class MenuKontekstowe extends JFrame {
       
    public MenuKontekstowe()
    {
        initComponents();
    }
    
    public void initComponents()
    {
        
        final JPopupMenu menuKontekstowe = new JPopupMenu();
        
            menuKontekstowe.add(new JMenuItem(new AbstractAction("Zamknij") {
            @Override
            public void actionPerformed(ActionEvent e) {
               System.exit(0);
            }
        }));
            menuKontekstowe.add(new JMenuItem("Kopiuj"));
            menuKontekstowe.add(new JMenuItem("Zapisz"));
            menuKontekstowe.add(new JMenuItem("Wklej"));
        
        this.setTitle("Menu kontekstowe");
        this.setBounds(300,300,200,200);
        this.getContentPane().addMouseListener(new MouseAdapter() {
        
            public void mouseReleased(MouseEvent e) {
                
                if (e.getClickCount() == 3 && e.getButton() == MouseEvent.BUTTON1 && e.isShiftDown())
                    JOptionPane.showMessageDialog(rootPane, "Ale się naklikałeś!");
                if (e.getButton() == MouseEvent.BUTTON3) menuKontekstowe.show(e.getComponent(),e.getX(), e.getY());
            }
            
        });
                
        this.setDefaultCloseOperation(EXIT_ON_CLOSE);
    }
    
    public static void main(String[] args) 
    {
         
        new MenuKontekstowe().setVisible(true);
        
    }
    
    }
