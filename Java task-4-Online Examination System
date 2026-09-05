```java
package exam;

import javax.swing.*;
import java.awt.*;

public class OnlineExaminationSystem extends JFrame {

    // =========================
    // QUESTIONS
    // =========================

    String[] questions = {
        "What is Java?",
        "Which keyword is used to create a class in Java?",
        "Which method is the starting point of a Java program?",
        "Which of these is not a Java keyword?",
        "Which data type is used to store whole numbers?",
        "Which symbol is used to end a statement in Java?",
        "Which keyword is used for inheritance?",
        "Which collection does not allow duplicate elements?",
        "Which package contains Swing classes?",
        "Which keyword is used to create an object?"
    };

    String[][] options = {
        {"Programming Language", "Database", "Operating System", "Browser"},
        {"class", "Class", "new", "create"},
        {"start()", "main()", "run()", "execute()"},
        {"static", "void", "main", "integer"},
        {"int", "float", "char", "boolean"},
        {".", ",", ";", ":"},
        {"extends", "inherit", "implements", "super"},
        {"List", "ArrayList", "Set", "Queue"},
        {"java.awt", "javax.swing", "java.io", "java.sql"},
        {"class", "new", "object", "create"}
    };

    // Correct option number
    // 0 = first option
    // 1 = second option
    // 2 = third option
    // 3 = fourth option

    int[] correctAnswers = {
        0, 0, 1, 3, 0,
        2, 0, 2, 1, 1
    };

    // =========================
    // USER ANSWERS
    // =========================

    int[] selectedAnswers = new int[10];

    int currentQuestion = 0;

    // 30 minutes = 1800 seconds
    int timeRemaining = 30 * 60;

    long examStartTime;

    // =========================
    // GUI COMPONENTS
    // =========================

    CardLayout cardLayout;

    JPanel mainPanel;

    JLabel timerLabel;

    JLabel questionLabel;

    JRadioButton option1;
    JRadioButton option2;
    JRadioButton option3;
    JRadioButton option4;

    ButtonGroup buttonGroup;

    Timer timer;

    // =========================
    // CONSTRUCTOR
    // =========================

    public OnlineExaminationSystem() {

        setTitle("Online Examination System");

        setSize(750, 550);

        setLocationRelativeTo(null);

        // Window close protection
        setDefaultCloseOperation(
                JFrame.DO_NOTHING_ON_CLOSE
        );

        addWindowListener(
                new java.awt.event.WindowAdapter() {

                    @Override
                    public void windowClosing(
                            java.awt.event.WindowEvent e) {

                        // If exam is running
                        if (timer != null
                                && timer.isRunning()) {

                            int result =
                                    JOptionPane.showConfirmDialog(
                                            OnlineExaminationSystem.this,
                                            "Are you sure you want to quit?",
                                            "Confirm Exit",
                                            JOptionPane.YES_NO_OPTION
                                    );

                            if (result
                                    == JOptionPane.YES_OPTION) {

                                timer.stop();

                                System.exit(0);
                            }

                        } else {

                            System.exit(0);
                        }
                    }
                }
        );

        // =========================
        // CARD LAYOUT
        // =========================

        cardLayout = new CardLayout();

        mainPanel = new JPanel(cardLayout);

        // Add screens
        mainPanel.add(
                createLoginPanel(),
                "LOGIN"
        );

        mainPanel.add(
                createProfilePanel(),
                "PROFILE"
        );

        mainPanel.add(
                createExamPanel(),
                "EXAM"
        );

        add(mainPanel);

        cardLayout.show(
                mainPanel,
                "LOGIN"
        );
    }

    // =========================================================
    // LOGIN SCREEN
    // =========================================================

    private JPanel createLoginPanel() {

        JPanel panel =
                new JPanel(new GridBagLayout());

        GridBagConstraints gbc =
                new GridBagConstraints();

        gbc.insets =
                new Insets(10, 10, 10, 10);

        JLabel title =
                new JLabel(
                        "ONLINE EXAMINATION SYSTEM"
                );

        title.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        25
                )
        );

        JLabel usernameLabel =
                new JLabel("Username:");

        JTextField usernameField =
                new JTextField(20);

        JLabel passwordLabel =
                new JLabel("Password:");

        JPasswordField passwordField =
                new JPasswordField(20);

        JButton loginButton =
                new JButton("Login");

        // Login button
        loginButton.addActionListener(e -> {

            String username =
                    usernameField.getText().trim();

            String password =
                    new String(
                            passwordField.getPassword()
                    );

            if (username.equals("admin")
                    && password.equals("1234")) {

                JOptionPane.showMessageDialog(
                        this,
                        "Login Successful!"
                );

                cardLayout.show(
                        mainPanel,
                        "PROFILE"
                );

            } else {

                JOptionPane.showMessageDialog(
                        this,
                        "Invalid Username or Password!",
                        "Login Error",
                        JOptionPane.ERROR_MESSAGE
                );
            }
        });

        // Title
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.gridwidth = 2;

        panel.add(title, gbc);

        // Username
        gbc.gridx = 0;
        gbc.gridy = 1;
        gbc.gridwidth = 1;

        panel.add(
                usernameLabel,
                gbc
        );

        gbc.gridx = 1;

        panel.add(
                usernameField,
                gbc
        );

        // Password
        gbc.gridx = 0;
        gbc.gridy = 2;

        panel.add(
                passwordLabel,
                gbc
        );

        gbc.gridx = 1;

        panel.add(
                passwordField,
                gbc
        );

        // Login
        gbc.gridx = 0;
        gbc.gridy = 3;
        gbc.gridwidth = 2;

        panel.add(
                loginButton,
                gbc
        );

        return panel;
    }

    // =========================================================
    // PROFILE SCREEN
    // =========================================================

    private JPanel createProfilePanel() {

        JPanel panel =
                new JPanel(new GridBagLayout());

        GridBagConstraints gbc =
                new GridBagConstraints();

        gbc.insets =
                new Insets(10, 10, 10, 10);

        JLabel title =
                new JLabel("UPDATE PROFILE");

        title.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        25
                )
        );

        JLabel nameLabel =
                new JLabel("Display Name:");

        JTextField nameField =
                new JTextField(20);

        JLabel passwordLabel =
                new JLabel("New Password:");

        JPasswordField passwordField =
                new JPasswordField(20);

        JButton startButton =
                new JButton("Start Exam");

        startButton.addActionListener(e -> {

            String displayName =
                    nameField.getText().trim();

            if (displayName.isEmpty()) {

                JOptionPane.showMessageDialog(
                        this,
                        "Please enter your display name."
                );

                return;
            }

            startExam();
        });

        // Title
        gbc.gridx = 0;
        gbc.gridy = 0;
        gbc.gridwidth = 2;

        panel.add(
                title,
                gbc
        );

        // Display name
        gbc.gridx = 0;
        gbc.gridy = 1;
        gbc.gridwidth = 1;

        panel.add(
                nameLabel,
                gbc
        );

        gbc.gridx = 1;

        panel.add(
                nameField,
                gbc
        );

        // Password
        gbc.gridx = 0;
        gbc.gridy = 2;

        panel.add(
                passwordLabel,
                gbc
        );

        gbc.gridx = 1;

        panel.add(
                passwordField,
                gbc
        );

        // Start button
        gbc.gridx = 0;
        gbc.gridy = 3;
        gbc.gridwidth = 2;

        panel.add(
                startButton,
                gbc
        );

        return panel;
    }

    // =========================================================
    // EXAM SCREEN
    // =========================================================

    private JPanel createExamPanel() {

        JPanel panel =
                new JPanel(new BorderLayout());

        // -------------------------
        // TIMER
        // -------------------------

        timerLabel =
                new JLabel("Time Remaining: 30:00");

        timerLabel.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        20
                )
        );

        timerLabel.setHorizontalAlignment(
                SwingConstants.CENTER
        );

        timerLabel.setBorder(
                BorderFactory.createEmptyBorder(
                        15, 10, 15, 10
                )
        );

        // -------------------------
        // QUESTION
        // -------------------------

        questionLabel =
                new JLabel();

        questionLabel.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        18
                )
        );

        questionLabel.setBorder(
                BorderFactory.createEmptyBorder(
                        15, 15, 15, 15
                )
        );

        // -------------------------
        // OPTIONS
        // -------------------------

        option1 =
                new JRadioButton();

        option2 =
                new JRadioButton();

        option3 =
                new JRadioButton();

        option4 =
                new JRadioButton();

        option1.setFont(
                new Font("Arial", Font.PLAIN, 16)
        );

        option2.setFont(
                new Font("Arial", Font.PLAIN, 16)
        );

        option3.setFont(
                new Font("Arial", Font.PLAIN, 16)
        );

        option4.setFont(
                new Font("Arial", Font.PLAIN, 16)
        );

        buttonGroup =
                new ButtonGroup();

        buttonGroup.add(option1);
        buttonGroup.add(option2);
        buttonGroup.add(option3);
        buttonGroup.add(option4);

        JPanel optionsPanel =
                new JPanel();

        optionsPanel.setLayout(
                new BoxLayout(
                        optionsPanel,
                        BoxLayout.Y_AXIS
                )
        );

        optionsPanel.setBorder(
                BorderFactory.createEmptyBorder(
                        10, 30, 10, 30
                )
        );

        optionsPanel.add(option1);
        optionsPanel.add(
                Box.createVerticalStrut(15)
        );

        optionsPanel.add(option2);
        optionsPanel.add(
                Box.createVerticalStrut(15)
        );

        optionsPanel.add(option3);
        optionsPanel.add(
                Box.createVerticalStrut(15)
        );

        optionsPanel.add(option4);

        // -------------------------
        // BUTTONS
        // -------------------------

        JButton previousButton =
                new JButton("Previous");

        JButton nextButton =
                new JButton("Next");

        JButton submitButton =
                new JButton("Submit Exam");

        JPanel bottomPanel =
                new JPanel();

        bottomPanel.setBorder(
                BorderFactory.createEmptyBorder(
                        10, 10, 15, 10
                )
        );

        bottomPanel.add(previousButton);
        bottomPanel.add(nextButton);
        bottomPanel.add(submitButton);

        // -------------------------
        // PREVIOUS BUTTON
        // -------------------------

        previousButton.addActionListener(e -> {

            saveAnswer();

            if (currentQuestion > 0) {

                currentQuestion--;

                loadQuestion();

            } else {

                JOptionPane.showMessageDialog(
                        this,
                        "This is the first question."
                );
            }
        });

        // -------------------------
        // NEXT BUTTON
        // -------------------------

        nextButton.addActionListener(e -> {

            saveAnswer();

            if (currentQuestion
                    < questions.length - 1) {

                currentQuestion++;

                loadQuestion();

            } else {

                JOptionPane.showMessageDialog(
                        this,
                        "This is the last question."
                );
            }
        });

        // -------------------------
        // SUBMIT BUTTON
        // -------------------------

        submitButton.addActionListener(e -> {

            saveAnswer();

            int result =
                    JOptionPane.showConfirmDialog(
                            this,
                            "Are you sure you want to submit?",
                            "Confirm Submission",
                            JOptionPane.YES_NO_OPTION
                    );

            if (result
                    == JOptionPane.YES_OPTION) {

                submitExam();
            }
        });

        // -------------------------
        // ADD COMPONENTS
        // -------------------------

        panel.add(
                timerLabel,
                BorderLayout.NORTH
        );

        JPanel centerPanel =
                new JPanel(new BorderLayout());

        centerPanel.add(
                questionLabel,
                BorderLayout.NORTH
        );

        centerPanel.add(
                optionsPanel,
                BorderLayout.CENTER
        );

        panel.add(
                centerPanel,
                BorderLayout.CENTER
        );

        panel.add(
                bottomPanel,
                BorderLayout.SOUTH
        );

        return panel;
    }

    // =========================================================
    // START EXAM
    // =========================================================

    private void startExam() {

        currentQuestion = 0;

        timeRemaining =
                30 * 60;

        selectedAnswers =
                new int[questions.length];

        // -1 means not attempted
        for (int i = 0;
             i < selectedAnswers.length;
             i++) {

            selectedAnswers[i] = -1;
        }

        examStartTime =
                System.currentTimeMillis();

        loadQuestion();

        cardLayout.show(
                mainPanel,
                "EXAM"
        );

        startTimer();
    }

    // =========================================================
    // LOAD QUESTION
    // =========================================================

    private void loadQuestion() {

        questionLabel.setText(
                "Question "
                + (currentQuestion + 1)
                + " of "
                + questions.length
                + ": "
                + questions[currentQuestion]
        );

        option1.setText(
                "A. "
                + options[currentQuestion][0]
        );

        option2.setText(
                "B. "
                + options[currentQuestion][1]
        );

        option3.setText(
                "C. "
                + options[currentQuestion][2]
        );

        option4.setText(
                "D. "
                + options[currentQuestion][3]
        );

        // Clear previous selection
        buttonGroup.clearSelection();

        // Restore selected answer
        int answer =
                selectedAnswers[currentQuestion];

        if (answer == 0) {

            option1.setSelected(true);

        } else if (answer == 1) {

            option2.setSelected(true);

        } else if (answer == 2) {

            option3.setSelected(true);

        } else if (answer == 3) {

            option4.setSelected(true);
        }
    }

    // =========================================================
    // SAVE ANSWER
    // =========================================================

    private void saveAnswer() {

        if (option1.isSelected()) {

            selectedAnswers[currentQuestion] = 0;

        } else if (option2.isSelected()) {

            selectedAnswers[currentQuestion] = 1;

        } else if (option3.isSelected()) {

            selectedAnswers[currentQuestion] = 2;

        } else if (option4.isSelected()) {

            selectedAnswers[currentQuestion] = 3;
        }
    }

    // =========================================================
    // TIMER
    // =========================================================

    private void startTimer() {

        if (timer != null) {

            timer.stop();
        }

        timer =
                new Timer(
                        1000,
                        e -> {

                            timeRemaining--;

                            int minutes =
                                    timeRemaining / 60;

                            int seconds =
                                    timeRemaining % 60;

                            timerLabel.setText(
                                    String.format(
                                            "Time Remaining: %02d:%02d",
                                            minutes,
                                            seconds
                                    )
                            );

                            // Time over
                            if (timeRemaining <= 0) {

                                timer.stop();

                                saveAnswer();

                                JOptionPane.showMessageDialog(
                                        this,
                                        "Time is over! Exam submitted automatically."
                                );

                                submitExam();
                            }
                        }
                );

        timer.start();
    }

    // =========================================================
    // SUBMIT EXAM
    // =========================================================

    private void submitExam() {

        if (timer != null) {

            timer.stop();
        }

        long endTime =
                System.currentTimeMillis();

        long timeTaken =
                (endTime - examStartTime)
                / 1000;

        int score = 0;

        int correct = 0;

        int incorrect = 0;

        int notAttempted = 0;

        // Calculate score
        for (int i = 0;
             i < questions.length;
             i++) {

            if (selectedAnswers[i] == -1) {

                notAttempted++;

            } else if (
                    selectedAnswers[i]
                    == correctAnswers[i]) {

                score++;

                correct++;

            } else {

                incorrect++;
            }
        }

        int minutes =
                (int) timeTaken / 60;

        int seconds =
                (int) timeTaken % 60;

        showResult(
                score,
                correct,
                incorrect,
                notAttempted,
                minutes,
                seconds
        );
    }

    // =========================================================
    // RESULT SCREEN
    // =========================================================

    private void showResult(
            int score,
            int correct,
            int incorrect,
            int notAttempted,
            int minutes,
            int seconds) {

        JPanel resultPanel =
                new JPanel(new BorderLayout());

        // -------------------------
        // TITLE
        // -------------------------

        JLabel title =
                new JLabel(
                        "EXAM RESULT",
                        SwingConstants.CENTER
                );

        title.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        28
                )
        );

        title.setBorder(
                BorderFactory.createEmptyBorder(
                        15, 10, 15, 10
                )
        );

        // -------------------------
        // SUMMARY
        // -------------------------

        JPanel summaryPanel =
                new JPanel();

        summaryPanel.setLayout(
                new BoxLayout(
                        summaryPanel,
                        BoxLayout.Y_AXIS
                )
        );

        summaryPanel.setBorder(
                BorderFactory.createEmptyBorder(
                        10, 30, 10, 30
                )
        );

        JLabel scoreLabel =
                new JLabel(
                        "Score: "
                        + score
                        + " out of "
                        + questions.length
                );

        JLabel timeLabel =
                new JLabel(
                        String.format(
                                "Time Taken: %02d:%02d",
                                minutes,
                                seconds
                        )
                );

        JLabel correctLabel =
                new JLabel(
                        "Correct Answers: "
                        + correct
                );

        JLabel incorrectLabel =
                new JLabel(
                        "Incorrect Answers: "
                        + incorrect
                );

        JLabel notAttemptedLabel =
                new JLabel(
                        "Not Attempted: "
                        + notAttempted
                );

        scoreLabel.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        18
                )
        );

        summaryPanel.add(scoreLabel);
        summaryPanel.add(timeLabel);
        summaryPanel.add(correctLabel);
        summaryPanel.add(incorrectLabel);
        summaryPanel.add(notAttemptedLabel);

        // -------------------------
        // BREAKDOWN
        // -------------------------

        JPanel breakdownPanel =
                new JPanel();

        breakdownPanel.setLayout(
                new BoxLayout(
                        breakdownPanel,
                        BoxLayout.Y_AXIS
                )
        );

        breakdownPanel.setBorder(
                BorderFactory.createEmptyBorder(
                        10, 30, 10, 30
                )
        );

        JLabel breakdownTitle =
                new JLabel(
                        "Question Breakdown"
                );

        breakdownTitle.setFont(
                new Font(
                        "Arial",
                        Font.BOLD,
                        18
                )
        );

        breakdownPanel.add(
                breakdownTitle
        );

        breakdownPanel.add(
                Box.createVerticalStrut(10)
        );

        // Add every question status
        for (int i = 0;
             i < questions.length;
             i++) {

            String status;

            if (selectedAnswers[i] == -1) {

                status =
                        "Question "
                        + (i + 1)
                        + ": Not Attempted";

            } else if (
                    selectedAnswers[i]
                    == correctAnswers[i]) {

                status =
                        "Question "
                        + (i + 1)
                        + ": Correct";

            } else {

                status =
                        "Question "
                        + (i + 1)
                        + ": Incorrect";
            }

            JLabel statusLabel =
                    new JLabel(status);

            statusLabel.setFont(
                    new Font(
                            "Arial",
                            Font.PLAIN,
                            15
                    )
            );

            breakdownPanel.add(
                    statusLabel
            );

            breakdownPanel.add(
                    Box.createVerticalStrut(5)
            );
        }

        JScrollPane scrollPane =
                new JScrollPane(
                        breakdownPanel
                );

        // -------------------------
        // LOGOUT
        // -------------------------

        JButton logoutButton =
                new JButton("Logout");

        logoutButton.addActionListener(e -> {

            cardLayout.show(
                    mainPanel,
                    "LOGIN"
            );
        });

        JPanel bottomPanel =
                new JPanel();

        bottomPanel.setBorder(
                BorderFactory.createEmptyBorder(
                        10, 10, 15, 10
                )
        );

        bottomPanel.add(
                logoutButton
        );

        // -------------------------
        // RESULT LAYOUT
        // -------------------------

        JPanel topPanel =
                new JPanel(
                        new BorderLayout()
                );

        topPanel.add(
                title,
                BorderLayout.NORTH
        );

        topPanel.add(
                summaryPanel,
                BorderLayout.CENTER
        );

        resultPanel.add(
                topPanel,
                BorderLayout.NORTH
        );

        resultPanel.add(
                scrollPane,
                BorderLayout.CENTER
        );

        resultPanel.add(
                bottomPanel,
                BorderLayout.SOUTH
        );

        // Remove old result screen if it exists
        for (Component component :
                mainPanel.getComponents()) {

            if (component instanceof JPanel) {

                // Nothing needed here
            }
        }

        mainPanel.add(
                resultPanel,
                "RESULT"
        );

        cardLayout.show(
                mainPanel,
                "RESULT"
        );
    }

    // =========================================================
    // MAIN METHOD
    // =========================================================

    public static void main(
            String[] args) {

        SwingUtilities.invokeLater(
                () -> {

                    OnlineExaminationSystem exam =
                            new OnlineExaminationSystem();

                    exam.setVisible(true);
                }
        );
    }
}
```
