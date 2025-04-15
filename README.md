import java.util.Scanner;

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
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            System.out.print("Enter your height in meters: ");
            double height = Double.parseDouble(scanner.nextLine());

            System.out.print("Enter your weight in kilograms: ");
            double weight = Double.parseDouble(scanner.nextLine());

            BMICalculator bmiCalc = new BMICalculator(height, weight);
            double bmi = bmiCalc.calculateBMI();
            String advice = bmiCalc.getHealthAdvice(bmi);

            System.out.printf("Your BMI is: %.2f\n%s\n", bmi, advice);
        } catch (NumberFormatException e) {
            System.out.println("Invalid input. Please enter numbers only.");
        } finally {
            scanner.close();
        }
    }
}
