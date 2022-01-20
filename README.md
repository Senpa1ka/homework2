# homework2
public class Main {
        public static void main(String[] args) {
            String[][] arr = new String[][]{{"4", "8", "14", "8"}, {"9", "8", "42", "54"}, {"98", "7", "4", "1"}, {"549", "1001", "-47", "-800"}};
            try {
                plus.plus(arr);
            } catch (MyArrayDataException e) {
                e.printStackTrace();
            } catch (MyArraySizeException e) {
                e.printStackTrace();
            }catch (Exception e) {
                System.out.println(e.getMessage());
            }

        }
    }
    
    public class plus {

    public static final int size = 4;

    public static int plus(String[][] arr) {
        if (arr == null) throw new NullPointerException("You give null");
        if (arr.length != size) {
            throw new MyArraySizeException("I need 4x4 only");
        }
        int sum = 0;
        for (int y = 0; y < arr.length; y++) {
            if (arr[y].length != size) {
                throw new MyArraySizeException("I need 4x4 only");
            }
            for (int x = 0; x < arr[y].length; x++) {
                try {
                    sum += Integer.parseInt(arr[y][x]);
                } catch (NumberFormatException e) {
                    throw new MyArrayDataException(String.format("Not number in [%d][%d]", x + 1, y + 1));
                }
            }
        }
        System.out.println("Sum" + sum);
        return sum;
    }

}

public class MyArrayDataException extends RuntimeException {

    public MyArrayDataException(String message) {
        super(message);
    }
}

public class MyArraySizeException extends RuntimeException {
        public MyArraySizeException(String message) {
            super(message);
        }
    }
