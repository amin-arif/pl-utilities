## **File Creation and Permission**

<br>

```java
import java.io.File;

private boolean setFilePermission(String path) {	
    	
    // Set file permission
    File file = new File(path);
    if (!file.exists()) {
        // file.mkdir() for single directory create
        return file.mkdirs() && // create directory with parent directories (if not exist)
            file.setExecutable(true) &&
            file.setWritable(true) && 
            file.setReadable(true);
    }			
    return true;
}
```