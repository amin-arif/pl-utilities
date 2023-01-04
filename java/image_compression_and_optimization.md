## **Image compression and optimization**

<br>

```java
import java.io.*;
import java.util.*;
import java.awt.image.*;
import javax.imageio.*;
import javax.imageio.stream.ImageOutputStream;


public void makeImageCompression() throws IOException {

    File input = new File("/home/arif/Pictures/arif_pic.jpg");
    BufferedImage image = ImageIO.read(input);

    File compressedImageFile = new File("/home/arif/Downloads/compress_arif_pic.jpg");
    OutputStream os = new FileOutputStream(compressedImageFile);

    Iterator<ImageWriter> writers =  ImageIO.getImageWritersByFormatName("jpg");
    ImageWriter writer = (ImageWriter) writers.next();

    ImageOutputStream ios = ImageIO.createImageOutputStream(os);
    writer.setOutput(ios);

    ImageWriteParam writeParam = writer.getDefaultWriteParam();
    
    writeParam.setCompressionMode(ImageWriteParam.MODE_EXPLICIT);
    writeParam.setCompressionQuality(0.5f);
    writer.write(null, new IIOImage(image, null, null), writeParam);
    
    os.close();
    ios.close();
    writer.dispose();
}
```

[source](https://www.tutorialspoint.com/java_dip/image_compression_technique.htm)