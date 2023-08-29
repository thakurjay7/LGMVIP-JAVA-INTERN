//JAVA DEVELOPER
//LGM VIRTUAL INTERNSHIP PROGRAM 2023

//BEGINNER LEVEL TASK
//CREATE A TIC-TAC-TOE GAME


import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

class TicTacToeGame {
    private JFrame frame;
    private JButton[] buttons;
    private JLabel statusLabel;
    private boolean isPlayerX = true;
    private int movesPlayed = 0;
    private Color xColor = Color.BLACK; // Default color for 'X'
    private Color oColor = Color.RED;   // Default color for 'O'

    private static final int[][] WINNING_COMBINATIONS = {
            {0, 1, 2}, {3, 4, 5}, {6, 7, 8}, // Rows
            {0, 3, 6}, {1, 4, 7}, {2, 5, 8}, // Columns
            {0, 4, 8}, {2, 4, 6}            // Diagonals
    };

    public TicTacToeGame() {
        frame = new JFrame("Tic-Tac-Toe Game");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 300);
        frame.setLayout(new BorderLayout());

        JPanel boardPanel = new JPanel();
        boardPanel.setLayout(new GridLayout(3, 3));

        buttons = new JButton[9];
        for (int i = 0; i < 9; i++) {
            buttons[i] = new JButton();
            buttons[i].setFont(new Font("Arial", Font.BOLD, 40));
            buttons[i].setFocusable(false);
            buttons[i].addActionListener(new ButtonClickListener());

            // Set background color
            buttons[i].setBackground(new Color(152, 238, 204)); // Custom color using RGB values

            // Set border color and style
            buttons[i].setBorder(BorderFactory.createLineBorder(Color.white, 2)); // Custom border color and thickness
            boardPanel.add(buttons[i]);
        }

        statusLabel = new JLabel("X's turn");
        statusLabel.setFont(new Font("Arial", Font.BOLD, 20));

        frame.add(boardPanel, BorderLayout.CENTER);
        frame.add(statusLabel, BorderLayout.SOUTH);

        frame.setVisible(true);
    }

    private class ButtonClickListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            JButton clickedButton = (JButton) e.getSource();
            if (clickedButton.getText().equals("") && !isGameOver()) {
                if (isPlayerX) {
                    clickedButton.setText("X");
                    clickedButton.setForeground(xColor); // Set 'X' color
                } else {
                    clickedButton.setText("O");
                    clickedButton.setForeground(oColor); // Set 'O' color

                }
                movesPlayed++;
                isPlayerX = !isPlayerX;
                updateStatusLabel();
                if (isGameOver()) {
                    showGameOverDialog();
                }
            }
        }
    }

    private boolean isGameOver() {
        if (movesPlayed >= 5) {
            for (int[] combination : WINNING_COMBINATIONS) {
                if (buttons[combination[0]].getText().equals(buttons[combination[1]].getText()) &&
                        buttons[combination[1]].getText().equals(buttons[combination[2]].getText()) &&
                        !buttons[combination[0]].getText().equals("")) {
                    return true;
                }
            }
        }
        return movesPlayed == 9;
    }

    private void updateStatusLabel() {
        if (isPlayerX) {
            statusLabel.setText("X's turn");
        } else {
            statusLabel.setText("O's turn");
        }
    }

    private void showGameOverDialog() {
        String message;
        if (isPlayerX) {
            message = "O wins!";
        } else {
            message = "X wins!";
        }
        if (movesPlayed == 9) {
            message = "It's a draw!";
        }
        int choice = JOptionPane.showOptionDialog(frame, message, "Game Over", JOptionPane.YES_NO_OPTION,
                JOptionPane.INFORMATION_MESSAGE, null, new String[]{"Restart", "Exit"}, "Restart");
        if (choice == 0) {
            resetGame();
        } else {
            System.exit(0);
        }
    }

    private void resetGame() {
        for (JButton button : buttons) {
            button.setText("");
        }
        isPlayerX = true;
        movesPlayed = 0;
        updateStatusLabel();
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(TicTacToeGame::new);
    }
}
