import java.util.Scanner;

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
