# android_poi_awt
This is a fork of windwardadmin/android-awt & andob/android-awt.
Code is took from Apache Harmony, Apache Commons Imaging and witwall/appengine-awt.

This project provides java.awt, javax.imagio and sfntly in jar file that is required by Apache POI on SXSSFWorkbook.
Due to memory heap size limitation XSSFWorkbook is not able to write large amount of data. Therefore we need to migrate to SXSSFWorkbook. 

However, there is no easy implementation but to compile another jar from andob/android-awt repository.

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

