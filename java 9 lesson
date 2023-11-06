import java.io.*;
import java.text.SimpleDateFormat;
import java.util.Date;

public class ShapeAreaCalculator {

    public static double calculateArea(String shape, double[] values) {
        if (shape.equals("Triangle")) {
            if (values.length == 3) {
                double a = values[0];
                double b = values[1];
                double c = values[2];
                double s = (a + b + c) / 2;
                return Math.sqrt(s * (s - a) * (s - b) * (s - c));
            }
        } else if (shape.equals("Rectangle")) {
            if (values.length == 2) {
                double a = values[0];
                double b = values[1];
                return a * b;
            }
        } else if (shape.equals("Square")) {
            if (values.length == 1) {
                double a = values[0];
                return a * a;
            }
        } else if (shape.equals("Circle")) {
            if (values.length == 1) {
                double r = values[0];
                return Math.PI * r * r;
            }
        }
        return 0; // Если фигура не распознана или данные некорректны
    }

    public static void main(String[] args) {
        String inputFilename = "input.txt";
        double totalArea = 0;

        try (BufferedReader reader = new BufferedReader(new FileReader(inputFilename))) {
            String line;
            while ((line = reader.readLine()) != null) {
                String[] data = line.split(" ");
                if (data.length >= 2) {
                    String shape = data[0];
                    double[] values = new double[data.length - 1];
                    for (int i = 1; i < data.length; i++) {
                        values[i - 1] = Double.parseDouble(data[i]);
                    }
                    double area = calculateArea(shape, values);
                    totalArea += area;
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd_HH-mm-ss");
        String timestamp = dateFormat.format(new Date());
        String outputFilename = "total_area_" + timestamp + ".txt";

        try (FileWriter writer = new FileWriter(outputFilename)) {
            writer.write("Total area of all shapes: " + totalArea);
            System.out.println("Результат записан в файл: " + outputFilename);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
