import java.util.List;

public class SuperPower {

    private static final int MOD = 1337;

    // Function to compute (a^b) % mod using modular exponentiation
    private static int powerMod(int a, int b, int mod) {
        int result = 1;
        a %= mod; // Reduce 'a' mod 'mod' first

        while (b > 0) {
            if (b % 2 == 1) {  // If b is odd, multiply result with a
                result = (result * a) % mod;
            }
            a = (a * a) % mod; // Square the base
            b /= 2;
        }
        return result;
    }

    // Function to compute super power using recursion
    private static int superPowHelper(int a, List<Integer> b, int index) {
        if (index < 0) return 1; // Base case: If b is empty, return 1

        int lastDigit = b.get(index); // Get the last digit
        int part1 = powerMod(a, lastDigit, MOD); // Compute (a^lastDigit) % MOD
        int part2 = powerMod(superPowHelper(a, b, index - 1), 10, MOD); // Compute ((a^rest) ^ 10) % MOD

        return (part1 * part2) % MOD;
    }

    public static int superPow(int a, List<Integer> b) {
        return superPowHelper(a, b, b.size() - 1);
    }

    // Main function
    public static void main(String[] args) {
        int a = 2;
        List<Integer> b = List.of(1, 0); // Example: 2^10 mod 1337
        System.out.println("Result: " + superPow(a, b)); // Output: 1024
    }
}




import java.util.HashSet;

public class LongestNiceSubstring {

    public static String longestNiceSubstring(String s) {
        if (s.length() < 2) return "";

        HashSet<Character> charSet = new HashSet<>();
        for (char ch : s.toCharArray()) {
            charSet.add(ch);
        }

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            // If one case exists but not the other, split and check recursively
            if (!charSet.contains(Character.toLowerCase(ch)) || !charSet.contains(Character.toUpperCase(ch))) {
                String left = longestNiceSubstring(s.substring(0, i));
                String right = longestNiceSubstring(s.substring(i + 1));

                return left.length() >= right.length() ? left : right;
            }
        }
        return s; // If the whole string is nice
    }

    public static void main(String[] args) {
        String s = "YazaAay";
        System.out.println("Longest Nice Substring: " + longestNiceSubstring(s)); // Output: "aAa"
    }
}



import java.util.List;

public class SuperPower {

    private static final int MOD = 1337;

    // Function to compute (a^b) % mod using modular exponentiation
    private static int powerMod(int a, int b, int mod) {
        int result = 1;
        a %= mod; // Reduce 'a' mod 'mod' first

        while (b > 0) {
            if (b % 2 == 1) {  // If b is odd, multiply result with a
                result = (result * a) % mod;
            }
            a = (a * a) % mod; // Square the base
            b /= 2;
        }
        return result;
    }

    // Function to compute super power using recursion
    private static int superPowHelper(int a, List<Integer> b, int index) {
        if (index < 0) return 1; // Base case: If b is empty, return 1

        int lastDigit = b.get(index); // Get the last digit
        int part1 = powerMod(a, lastDigit, MOD); // Compute (a^lastDigit) % MOD
        int part2 = powerMod(superPowHelper(a, b, index - 1), 10, MOD); // Compute ((a^rest) ^ 10) % MOD

        return (part1 * part2) % MOD;
    }

    public static int superPow(int a, List<Integer> b) {
        return superPowHelper(a, b, b.size() - 1);
    }

    // Main function
    public static void main(String[] args) {
        int a = 2;
        List<Integer> b = List.of(1, 0); // Example: 2^10 mod 1337
        System.out.println("Result: " + superPow(a, b)); // Output: 1024
    }
}
