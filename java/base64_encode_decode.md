## **Base64 Encode and Decode**

</br>

```java
import java.util.Base64;

private String encode(byte[] data) {
    return Base64.getEncoder().encodeToString(data);
}

private byte[] decode(String encodedData) {
    return Base64.getDecoder().decode(encodedData);
}
```
