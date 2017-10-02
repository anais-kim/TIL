## How to change Decimal to Binary?
It's quite simple in java. We can use API.
```java
Integer.toBinaryString(25); //11001
```
How about Binary to Decimal? It's also simple.
```java
Integer.parseInt("11001", 2); //25
```
If we can't use API, we should do it like...
```java
private String decimalToBinary(int decimal) {
    if (decimal == 1) return "1";
    int quotient = decimal / 2;
    int remain = decimal % 2;
    return decimalToBinary(quotient) + String.valueOf(remain);
}

private int binaryToDecimal(String binary) {
    int decimal = 0;
    for (int i = 0; i < binary.length(); i++) {
        if(binary.charAt(i) == '1') {
            decimal += Math.pow(2, (binary.length()-i-1));
        }
    }
    return decimal;
}
```
