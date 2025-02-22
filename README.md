AMON TANUI
EB3/61576/22
import java.util.HashMap;

public class FactorialFibonacci {
    private static HashMap<Integer, Long> fibCache = new HashMap<>();

    public static long factorial(int n) {
        if (n == 0 || n == 1) return 1;
        return n * factorial(n - 1);
    }

    public static long fibonacci(int n) {
        if (n <= 0) return 0;
        if (n == 1) return 1;
        if (fibCache.containsKey(n)) return fibCache.get(n);
        long result = fibonacci(n - 1) + fibonacci(n - 2);
        fibCache.put(n, result);
        return result;
    }

    public static void measureRuntime(String functionName, int n) {
        long startTime = System.nanoTime();
        long result = functionName.equals("factorial") ? factorial(n) : fibonacci(n);
        long endTime = System.nanoTime();
        double elapsedTime = (endTime - startTime) / 1e6;
        System.out.println(functionName + "(" + n + ") = " + result + ", Time taken: " + elapsedTime + " ms");
    }

    public static void main(String[] args) {
        int n = 10; // Change this value to test different inputs
        measureRuntime("factorial", n);
        measureRuntime("fibonacci", n);
    }
}
