import javax.swing.JOptionPane;

class BMICalculator {
    private double height;
    private double weight;

    public BMICalculator(double height, double weight) {
        this.height = height;
        this.weight = weight;
    }

    public double calculateBMI() {
        return weight / (height * height);
    }

    public String getHealthAdvice(double bmi) {
        if (bmi < 18.5) {
            return "You are underweight. Eat a balanced diet and consult a doctor if needed.";
        } else if (bmi < 24.9) {
            return "You have a normal weight. Keep up the good work!";
        } else if (bmi < 29.9) {
            return "You are overweight. Consider regular exercise and a healthy diet.";
        } else {
            return "You are obese. It's important to consult a healthcare professional.";
        }
    }

    public static boolean isValidInput(double height, double weight) {
        return height > 0 && weight > 0;
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            double height = Double.parseDouble(JOptionPane.showInputDialog("Enter your height in meters:"));
            double weight = Double.parseDouble(JOptionPane.showInputDialog("Enter your weight in kilograms:"));

            if (!BMICalculator.isValidInput(height, weight)) {
                JOptionPane.showMessageDialog(null, "Height and weight must be positive numbers.");
                return;
            }

            BMICalculator bmiCalc = new BMICalculator(height, weight);
            double bmi = bmiCalc.calculateBMI();
            String advice = bmiCalc.getHealthAdvice(bmi);

            JOptionPane.showMessageDialog(null, String.format("Your BMI is: %.2f\n%s", bmi, advice));
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(null, "Invalid input. Please enter numbers only.");
        }
    }
}