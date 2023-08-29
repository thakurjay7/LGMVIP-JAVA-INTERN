//JAVA DEVELOPER
//LGM VIRTUAL INTERNSHIP PROGRAM 2023

//INTERMEDIATE LEVEL TASK
//CREATE A SCIENTIFIC CALCULATOR

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class ScientificCalculator {
    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JFrame frame = new CalculatorFrame();
            frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
            frame.setVisible(true);
        });
    }
}

class CalculatorFrame extends JFrame {
    private JTextField tfText;
    private boolean hasNumber = true;
    private String equalOp = "=";
    private CalculatorOp op = new CalculatorOp();

    public CalculatorFrame() {
        tfText = new JTextField("", 12);
        tfText.setHorizontalAlignment(JTextField.RIGHT);
        tfText.setFont(new Font("Arial", Font.PLAIN, 20));

        JPanel mainPanel = new JPanel(new BorderLayout());

        JPanel buttonPanel = createButtonPanel();
        JPanel operatorPanel = createOperatorPanel();

        mainPanel.add(tfText, BorderLayout.NORTH);
        mainPanel.add(buttonPanel, BorderLayout.CENTER);
        mainPanel.add(operatorPanel, BorderLayout.EAST);

        setContentPane(mainPanel);
        setTitle("Scientific Calculator");
        pack();
        setResizable(false);
    }

    private JPanel createButtonPanel() {
        JPanel buttonPanel = new JPanel();
        buttonPanel.setLayout(new GridBagLayout());

        GridBagConstraints gbc = new GridBagConstraints();
        gbc.fill = GridBagConstraints.BOTH;
        gbc.weightx = 1.0;
        gbc.weighty = 1.0;
        gbc.insets = new Insets(1, 1, 1, 1); // Adjust the values to set the margin

        for (int i = 0; i <= 9; i++) {
            addButton(buttonPanel, Integer.toString(i), gbc);
        }

        return buttonPanel;
    }

    private void addButton(JPanel panel, String label, GridBagConstraints gbc) {
        JButton button = new JButton(label);
        button.setFont(new Font("Arial", Font.PLAIN, 20));
        button.addActionListener(new NumberListener());

        Color customColor = new Color(147, 177, 166); // RGB values
        button.setBackground(customColor); //Set Background color of buttons


        panel.add(button, gbc);


    }

    private JPanel createOperatorPanel() {
        JPanel operatorPanel = new JPanel();
        operatorPanel.setLayout(new GridLayout(6, 1, 2, 2));



        addOperatorButton(operatorPanel, "sin");
        addOperatorButton(operatorPanel, "cos");
        addOperatorButton(operatorPanel, "tan");
        addOperatorButton(operatorPanel, "sec");
        addOperatorButton(operatorPanel, "cosec");
        addOperatorButton(operatorPanel, "log");
        addOperatorButton(operatorPanel, "+");
        addOperatorButton(operatorPanel, "-");
        addOperatorButton(operatorPanel, "*");
        addOperatorButton(operatorPanel, "/");
        addOperatorButton(operatorPanel, "=");
        addOperatorButton(operatorPanel, "C");

        return operatorPanel;
    }

    private void addOperatorButton(JPanel panel, String label) {
        JButton button = new JButton(label);
        button.setFont(new Font("Arial", Font.PLAIN, 20));
        button.addActionListener(new OperatorListener());

        Color customColor = new Color(92, 131, 116); // RGB values
        button.setBackground(customColor);// Change the color of the operator button


        panel.add(button);


    }

    class OperatorListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            String displayText = tfText.getText();
            String operator = e.getActionCommand();

            if (operator.equals("sin")) {
                tfText.setText("" + Math.sin(Double.parseDouble(displayText)));
            } else if (operator.equals("cos")) {
                tfText.setText("" + Math.cos(Double.parseDouble(displayText)));
            } else if (operator.equals("tan")) {
                tfText.setText("" + Math.tan(Double.parseDouble(displayText)));
            } else if (operator.equals("sec")) {
                tfText.setText("" + (1.0 / Math.cos(Double.parseDouble(displayText))));
            } else if (operator.equals("cosec")) {
                tfText.setText("" + (1.0 / Math.sin(Double.parseDouble(displayText))));
            } else if (operator.equals("log")) {
                tfText.setText("" + Math.log(Double.parseDouble(displayText)));
            } else if (operator.equals("C") || operator.equals("CE")) {
                tfText.setText("");
                hasNumber = true;
            } else if (operator.equals("=")) {
                if (!hasNumber) {
                    calculate();
                    hasNumber = true;
                }
            } else {
                if (!hasNumber) {
                    calculate();
                    hasNumber = true;
                }
                equalOp = operator;
            }
        }

        private void calculate() {
            String displayText = tfText.getText();
            if (equalOp.equals("+")) {
                op.add(displayText);
            } else if (equalOp.equals("-")) {
                op.subtract(displayText);
            } else if (equalOp.equals("*")) {
                op.multiply(displayText);
            } else if (equalOp.equals("/")) {
                op.divide(displayText);
            }
            tfText.setText("" + op.getTotalString());
        }
    }


    class NumberListener implements ActionListener {
        public void actionPerformed(ActionEvent event) {
            String digit = event.getActionCommand();

            if (hasNumber) {
                tfText.setText(digit);
                hasNumber = false;
            } else {
                tfText.setText(tfText.getText() + digit);
            }
        }
    }

    public class CalculatorOp {
        private double total;
        public CalculatorOp() {
            total = 0;
        }
        public String getTotalString() {
            return "" + total;
        }
        public void setTotal(String n) {
            total = Double.parseDouble(n);
        }
        public void add(String n) {
            total += Double.parseDouble(n);
        }
        public void subtract(String n) {
            total -= Double.parseDouble(n);
        }
        public void multiply(String n) {
            total *= Double.parseDouble(n);
        }
        public void divide(String n) {
            double num = Double.parseDouble(n);
            if (num != 0) {
                total /= num;
            }
        }
    }
}
