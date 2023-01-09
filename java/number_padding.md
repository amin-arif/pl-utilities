## **Number Padding**

<br>

1. Using String format method

    ```java
    int num = 245;
    // Total 6 digits (000 + 245)
    String paddingNum = String.format("%06d", num); // output: 000245
    ```

    [useful resource](https://www.javatpoint.com/java-string-format)

2. Using DecimalFormatSymbols

    ```java
    int num = 245;
    DecimalFormatSymbols symbols = new DecimalFormatSymbols();
    DecimalFormat decimalFormat = new DecimalFormat("000000", symbols);
    String paddingNum = decimalFormat.format(num);  // output: 000245
    ```

