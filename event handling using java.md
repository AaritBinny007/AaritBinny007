import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class VoterEligibilityGUI extends JFrame {
    private JTextField nameField;
    private JTextField ageField;
    private JCheckBox citizenCheckBox;
    private JButton submitButton;

    public VoterEligibilityGUI() {
        setTitle("Voter Eligibility Checker");
        setSize(400, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Creating components
        JLabel nameLabel = new JLabel("Name:");
        JLabel ageLabel = new JLabel("Age:");
        JLabel citizenLabel = new JLabel("Citizen:");

        nameField = new JTextField();
        ageField = new JTextField();
        citizenCheckBox = new JCheckBox();

        submitButton = new JButton("Submit");
        submitButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                checkEligibility();
            }
        });

        // Creating layout
        setLayout(new GridLayout(4, 2));

        // Adding components to the frame
        add(nameLabel);
        add(nameField);
        add(ageLabel);
        add(ageField);
        add(citizenLabel);
        add(citizenCheckBox);
        add(submitButton);

        setVisible(true);
    }

    private void checkEligibility() {
        String name = nameField.getText();
        String ageText = ageField.getText();

        // Check if age is a number
        try {
            int age = Integer.parseInt(ageText);

            // Check eligibility criteria (e.g., age greater than 18 and citizenship)
            if (age > 18 && citizenCheckBox.isSelected()) {
                JOptionPane.showMessageDialog(this, "Details submitted successfully", "Eligible", JOptionPane.INFORMATION_MESSAGE);
            } else {
                JOptionPane.showMessageDialog(this, "Not eligible", "Not Eligible", JOptionPane.WARNING_MESSAGE);
            }

        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Please enter a valid age", "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new VoterEligibilityGUI();
            }
        });
    }
}
