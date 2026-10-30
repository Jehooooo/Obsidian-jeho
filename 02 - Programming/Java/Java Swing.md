---
tags: [learning, java]
topic: Java Swing
category: Programming Languages
---

# ☕ Java Swing

## What Is It?

Java Swing is a **GUI (Graphical User Interface) toolkit** for building desktop applications in Java. It provides components like buttons, text fields, tables, menus, and dialog boxes. Swing is part of Java's standard library, so you don't need to install anything extra.

Think of Swing as a set of building blocks for creating desktop apps — like how HTML/CSS builds web pages, Swing builds desktop windows.

## Why Is It Important?

- **Desktop applications** — needed for academic projects and CS courses
- **Event-driven programming** — teaches how UI interactions work
- **Foundation for understanding UI** — concepts transfer to web and mobile development
- **Academic requirement** — commonly taught in CS programs

## Syntax / Concepts

### Basic Window
```java
import javax.swing.*;

public class MyApp {
    public static void main(String[] args) {
        JFrame frame = new JFrame("My Application");
        frame.setSize(600, 400);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocationRelativeTo(null);  // Center on screen
        frame.setVisible(true);
    }
}
```

### Common Components
```java
JLabel label = new JLabel("Hello, Jeho!");      // Text label
JButton button = new JButton("Click Me");       // Button
JTextField textField = new JTextField(20);       // Text input
JTextArea textArea = new JTextArea(5, 20);       // Multi-line text
JComboBox<String> dropdown = new JComboBox<>(new String[]{"Pending", "In Progress", "Solved"});
JTable table = new JTable(data, columnNames);    // Data table
```

### Event Handling
```java
button.addActionListener(e -> {
    String input = textField.getText();
    label.setText("You typed: " + input);
});
```

### Layout Managers
```java
panel.setLayout(new BorderLayout());   // North, South, East, West, Center
panel.setLayout(new FlowLayout());     // Left to right, wrap
panel.setLayout(new GridLayout(3, 2)); // Grid of rows and columns
```

## Example

```java
import javax.swing.*;
import java.awt.*;

public class IncidentReporter extends JFrame {
    private JTextField titleField;
    private JTextField locationField;
    private JComboBox<String> statusBox;
    private JTextArea outputArea;
    
    public IncidentReporter() {
        setTitle("Incident Reporter");
        setSize(500, 400);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Input panel
        JPanel inputPanel = new JPanel(new GridLayout(3, 2, 5, 5));
        inputPanel.add(new JLabel("Title:"));
        titleField = new JTextField();
        inputPanel.add(titleField);
        inputPanel.add(new JLabel("Location:"));
        locationField = new JTextField();
        inputPanel.add(locationField);
        inputPanel.add(new JLabel("Status:"));
        statusBox = new JComboBox<>(new String[]{"Pending", "In Progress", "Solved"});
        inputPanel.add(statusBox);
        
        // Submit button
        JButton submitBtn = new JButton("Submit Report");
        submitBtn.addActionListener(e -> submitReport());
        
        // Output area
        outputArea = new JTextArea();
        outputArea.setEditable(false);
        
        add(inputPanel, BorderLayout.NORTH);
        add(submitBtn, BorderLayout.CENTER);
        add(new JScrollPane(outputArea), BorderLayout.SOUTH);
        
        setVisible(true);
    }
    
    private void submitReport() {
        String report = String.format("[%s] %s at %s\n",
            statusBox.getSelectedItem(), titleField.getText(), locationField.getText());
        outputArea.append(report);
        titleField.setText("");
        locationField.setText("");
    }
    
    public static void main(String[] args) {
        new IncidentReporter();
    }
}
```

## Common Mistakes

1. **Not using `setVisible(true)`** — your window won't appear without this
2. **Forgetting `EXIT_ON_CLOSE`** — the program keeps running after closing the window
3. **Not using layout managers** — components stack on top of each other
4. **Blocking the UI thread** — long operations freeze the UI; use SwingWorker

## Practice

- [ ] Create a basic window with a label and a button
- [ ] Build a simple form with text fields and a submit button
- [ ] Create a table that displays data from an array
- [ ] Build a calculator with buttons and a text display
- [ ] Add menu bar with File and Help menus

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Java OOP]]
- [[Software Engineering]]
