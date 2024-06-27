android_poi_sxssf_awt

This is a fork of windwardadmin/android-awt & andob/android-awt.
Code is took from Apache Harmony, Apache Commons Imaging and witwall/appengine-awt.

This project provides java.awt, javax.imagio and sfntly in jar file that is required by Apache POI on SXSSFWorkbook.
Due to memory heap size limitation XSSFWorkbook is not able to write large amount of data. Therefore we need to migrate to SXSSFWorkbook. 

Without AWT and sfntly you will get such error below.

````
// Without AWT
java.lang.NoClassDefFoundError: Failed resolution of: Ljava/awt/font/FontRenderContext;
// Without sfntly
java.lang.NoClassDefFoundError: Failed resolution of: Lcom/google/typography/font/sfntly/FontFactory;
````

Thanks to andob/android-awt library but we will getting error on \awtcompat\src\main\java\java\awt\font\sfntly\SfntlyFontPeer.java on the font resource.

There is no OpenSans-Regular.ttf embeded in the library. So I have created the jar using Android Studio and include the font using zip software.

However, there is no easy implementation but to compile another jar from andob/android-awt repository and apply as library.

![image](https://github.com/bkhong87/android_poi_sxssf_awt/assets/16471081/750c0e96-ce54-4474-8490-18b6cb68e9b2)

I have change the code ~~InputStream ttfInput = getClass().getResourceAsStream("OpenSans-Regular.ttf");~~ to below so library could read the font from classpath.
````
InputStream ttfInput = getClass().getResourceAsStream("/opensans.ttf");
````


Note*: I am new to github but wish to share the capability of SXSSFWorkbook on Android platform.

1) Download awtcompat.jar & sfntly-1.0.0.jar place inside libs/
````
  <Project>
    <Project Name>
      libs/awtcompat.jar
      libs/sfntly-1.0.0.jar
````
2) Implement apache dependencies
````
dependencies {
  implementation files('/libs/awtcompat.jar')
  implementation files('/libs/sfntly-1.0.0.jar')

  // Apache POI
  implementation 'org.apache.poi:poi:5.2.5'
  implementation 'org.apache.poi:poi-ooxml:5.2.5'
  implementation 'org.apache.xmlbeans:xmlbeans:5.2.1'
  implementation 'javax.xml.stream:stax-api:1.0-2'
  implementation 'com.fasterxml:aalto-xml:1.3.3'
}
````

