# **Date conversion among sql, util and string**

</br>

## 1. String Date to Util Date

```java
String strDate = "2023-01-24";

SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
java.util.Date utilDate = formatter.parse(strDate);
```

</br>

## 2. String Date to SQL Date

```java
String strDate = "2023-01-24";

SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
java.util.Date utilDate = formatter.parse(strDate);
java.sql.Date sqlDate = new java.sql.Date(utilDate.getTime());
```

</br>

## 3. Util Date to SQL Date

```java
Date utilDate = new Date(); // Current date
java.sql.Date sqlDate = new java.sql.Date(utilDate.getTime());
```

</br>

## 4. SQL Date to Util Date

```java
Date utilDate = new Date(sqlDate.getTime());
```

</br>

## 5. Util Date to String Date

```java
Date utilDate = new Date();
SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
String formattedStrDate = formatter.format(utilDate);  // Formatted date
String strDate = utilDate.toString();  // Without format
//---Same way for SQL Date to String Date---
```
