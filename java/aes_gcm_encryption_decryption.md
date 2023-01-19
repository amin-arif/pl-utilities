## **AES GCM Encryption and Decryption**

</br>

**1. Auto generate key**

Learn more: [Source 1](https://www.section.io/engineering-education/implementing-aes-encryption-and-decryption-in-java/) [Source 2](https://www.javainterviewpoint.com/java-aes-256-gcm-encryption-and-decryption/)

```java

```

</br>

**2. Custom key**

Learn more: [Source 1](https://www.javatpoint.com/aes-256-encryption-in-java) [Source 2](https://stackoverflow.com/questions/3451670/java-aes-and-using-my-own-key)

```java
import javax.crypto.SecretKey;
import javax.crypto.Cipher;
import javax.crypto.spec.GCMParameterSpec;
import javax.crypto.spec.IvParameterSpec;
import javax.crypto.spec.SecretKeySpec;
import java.util.Base64;

public class AESEncryptionDecryption 
{
    private static final int DATA_LENGTH = 128;
    private static final byte[] INITIALIZATION_VECTOR = {9, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 6};
	private static final String SALT_VALUE = "asdfghjklmnbvcxz"; // length 16
	// private static final byte[] SALT_VALUE = new byte[] {'0','2','3','4','5','6','7','8','9','1','2','3','4','5','6','7'};

	// Generate a secret key using AES algorithm
    private static SecretKey generateKey() throws Exception {  	
    	return new SecretKeySpec(SALT_VALUE.getBytes(), "AES");
    }
    
    // Performs Encryption
    public static String encrypt(String data) throws Exception {
    	
		SecretKey key = generateKey();
        Cipher chiper = Cipher.getInstance("AES/GCM/NoPadding");
        
		IvParameterSpec ivSpec = new IvParameterSpec(INITIALIZATION_VECTOR);
        GCMParameterSpec spec = new GCMParameterSpec(DATA_LENGTH, ivSpec.getIV());       
        chiper.init(Cipher.ENCRYPT_MODE, key, spec);
        
        byte[] encryptedData = chiper.doFinal(data.getBytes());       
        return Base64.getEncoder().encodeToString(encryptedData);
    }

    // Performs Decryption
    public static String decrypt(String encryptedData) throws Exception {

		SecretKey key = generateKey();
        Cipher chiper = Cipher.getInstance("AES/GCM/NoPadding");
        
		IvParameterSpec ivSpec = new IvParameterSpec(INITIALIZATION_VECTOR);
        GCMParameterSpec spec = new GCMParameterSpec(DATA_LENGTH, ivSpec.getIV()); 
        chiper.init(Cipher.DECRYPT_MODE, key, spec);   
        
        byte[] decodedData = Base64.getDecoder().decode(encryptedData);
        byte[] decryptedData = chiper.doFinal(decodedData);       
        return new String(decryptedData);
    }


    // Performs Encryption & Decryption 
    public static void main(String[] args) throws Exception {
    	
            String plainText = "Happy learning! Happy coding!";
            String encryptedText = AESEncryptionDecryption.encrypt(plainText);
            String decryptedText = AESEncryptionDecryption.decrypt(encryptedText);

            System.out.println("Plain Text : " + plainText);
            System.out.println("Encrypted Text : " + encryptedText);
            System.out.println("Decrypted Text : " + decryptedText);
    }
}
```
