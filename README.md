

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

package usersdatabase;
import java.net.URL;
import java.util.ResourceBundle;
import javafx.event.ActionEvent;
import javafx.fxml.FXML;
import javafx.fxml.Initializable;
import javafx.scene.control.Label;
import com.jfoenix.controls.JFXButton;
import com.jfoenix.controls.JFXPasswordField;
import com.jfoenix.controls.JFXTextField;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import javafx.fxml.FXMLLoader;
import javafx.scene.Parent;
import javafx.scene.Scene;
import javafx.stage.Stage;
/**
 *
 * @author Josh
 */
public class LoginController implements Initializable {
    
    @FXML
    private JFXTextField usernm;
    @FXML
    private JFXPasswordField pswd;
    @FXML
    private JFXButton login;
    @FXML
    private JFXButton reg;
    
    @Override
    public void initialize(URL url, ResourceBundle rb) {
        // TODO
    }    

    @FXML
    private void registerHandler(ActionEvent event) {
    }

    @FXML
    private void LoginHandler(ActionEvent event) {
       
        String sql="SELECT * FROM users WHERE Username=? AND Password=?";
        DatabaseConnection databaseConnection=new DatabaseConnection();
        try {
            try (Connection connection = databaseConnection.getConnection()) {
                PreparedStatement preparedStatement = connection.prepareStatement(sql);
                preparedStatement.setString(1, usernm.getText());
                preparedStatement.setString(2, pswd.getText());
                ResultSet resultset = preparedStatement.executeQuery();
                if (resultset.next()) {
                    System.out.println("logged");
                    try {
                        FXMLLoader fxmlLoader = new FXMLLoader(getClass().getResource("Dashboard.fxml"));
                        Parent root1 = (Parent) fxmlLoader.load();
                        Stage stage = new Stage();
                        stage.setScene(new Scene(root1));
                        stage.show();
                        Stage loStage=(Stage) login.getScene().getWindow();
                        loStage.hide();
                    } catch (Exception e) {
                    }
                }
                else
                {
                    System.out.println("not logged");
                }}
         
        } catch (Exception e) {
            System.out.println(e.toString());
        }
    }
    
}
