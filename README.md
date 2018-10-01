

import java.awt.event.ActionEvent;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

/**
 *
 * @author Hellen Simam
 */
public class login {
    
    private JLabel namelable,passwordlabel;
    private JTextField name ,password;
    private JButton login,clear;
    private JPanel mypanel;

    public static void main(String[] args) {
        
        JFrame myframe=new JFrame("LOGIN HERE");
        JPanel mypanel=new JPanel();
        JLabel namelabel=new JLabel("USERNAME:");
        JTextField name=new JTextField();
        name.setColumns(25);
        
        
        JLabel passwordlabel=new JLabel("PASSWORD:");
        JTextField password=new JTextField();
        password.setColumns(25);
        
        
        JButton login=new JButton("LOGIN");
         login.setText("Login");
         login.addActionListener((ActionEvent e) -> {
        });
         
         
        JButton clear=new JButton("CLEAR");
         clear.setText("Clear");
        clear.addActionListener((ActionEvent e) -> {
        });
        
        mypanel.add(namelabel);
        mypanel.add(name);
        mypanel.add(passwordlabel);
        mypanel.add(password);
        mypanel.add(clear);
        mypanel.add(login);
        myframe.add(mypanel);
        myframe.setSize(40,30);
        myframe.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myframe.setVisible(true);
         
        
        
        
        }
     

    
}
