import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SwingDemo {

    public SwingDemo() {
        JFrame jfrm = new JFrame("Divider App");
        jfrm.setSize(275, 200); // Increase height for better UI spacing
        jfrm.setLayout(new FlowLayout());
        jfrm.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JLabel jlab = new JLabel("Enter the divider and dividend:");
        JTextField ajtf = new JTextField(8);
        JTextField bjtf = new JTextField(8);
        JButton button = new JButton("Calculate");
        JLabel err = new JLabel();
        JLabel alab = new JLabel();
        JLabel blab = new JLabel();
        JLabel anslab = new JLabel();

        // Set error label font and color
        err.setForeground(Color.RED);
        err.setFont(new Font("Arial", Font.BOLD, 12));

        jfrm.add(jlab);
        jfrm.add(ajtf);
        jfrm.add(bjtf);
        jfrm.add(button);
        jfrm.add(alab);
        jfrm.add(blab);
        jfrm.add(anslab);
        jfrm.add(err);  // Add error label at the end to make it stand out

        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent evt) {
                try {
                    int a = Integer.parseInt(ajtf.getText());
                    int b = Integer.parseInt(bjtf.getText());
                    int ans = a / b;

                    alab.setText("A = " + a);
                    blab.setText("B = " + b);
                    anslab.setText("Ans = " + ans);
                    err.setText(""); // Clear any previous error messages

                } catch (NumberFormatException e) {
                    alab.setText("");
                    blab.setText("");
                    anslab.setText("");
                    err.setText("Enter Only Integers!");
                    JOptionPane.showMessageDialog(jfrm, "Invalid input! Please enter integers only.", "Input Error", JOptionPane.ERROR_MESSAGE);

                } catch (ArithmeticException e) {
                    alab.setText("");
                    blab.setText("");
                    anslab.setText("");
                    err.setText("B should be NON zero!");
                    JOptionPane.showMessageDialog(jfrm, "Cannot divide by zero!", "Math Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        jfrm.setVisible(true);
    }

    public static void main(String args[]) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new SwingDemo();
            }
        });
    }
}
