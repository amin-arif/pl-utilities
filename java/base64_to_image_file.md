## **Base64 to image file conversion**

<br>

```java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.Base64;

public void makeBase64ToImageFile(String base64Img, String path) throws IOException {
        
    byte[] decodeImgBytes = Base64.getDecoder()
            .decode(base64Img.getBytes(StandardCharsets.UTF_8));				
    Path destinationFile = Paths.get(path, "photo.jpg");				
    Files.write(destinationFile, decodeImgBytes);
}
```