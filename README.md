# J1.L.P0002
import java.util.*;

public class SelectionSort {
    public static void main(String[] args) {
        int a[] = inputArray();
        System.out.println("Before sorted:");
        outputArray(a);
        checkArray(a);
        System.out.println("After sorted:");
        outputArray(a);
    }

   public static int[] inputArray() {
    Scanner sc = new Scanner(System.in);
    Random r = new Random();
    int n;
    int[] a = null;
    boolean isValidInput = false;

    do {
        try {
            System.out.println("Input the number of elements in the array:");
            n = sc.nextInt();
            if (n > 0) {
                a = new int[n];
                isValidInput = true;
                for (int i = 0; i < n; i++) {
                    a[i] = r.nextInt(n);  
                }
            } else {
                System.out.println("Number of elements should be greater than 0.");
            }
        } catch (Exception e) {
            System.out.println("Invalid input. Please enter a valid number.");
            sc.nextLine(); // Clear the input buffer
        }
    } while (!isValidInput);

    return a;
}

    public static void outputArray(int[] a) {
        for (int i = 0; i < a.length; i++) {
            System.out.print(a[i]);
            if (i < a.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println();
    }

    public static void selectionSort(int[] a) {
        for (int i = 0; i < a.length - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < a.length; j++) {
                if (a[j] < a[minIndex]) {
                    minIndex = j;
                }
            }
            if (minIndex != i) {
                int temp = a[i];
                a[i] = a[minIndex];
                a[minIndex] = temp;
            }
        }
    }

    public static void checkArray(int[] a) {
        boolean isSorted = true;
        for (int i = 0; i < a.length - 1; i++) {
            if (a[i] > a[i + 1]) {
                isSorted = false;
                break;
            }
        }
        if (isSorted) {
            System.out.println("Array already sorted");
        } else {
            selectionSort(a);
        }
    }
}
