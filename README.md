# android_poi_awt
This is a fork of windwardadmin/android-awt & andob/android-awt

This project provides java.awt, javax.imagio and sfntly in jar file that is required by Apache POI on SXSSF workbook.

dependencies {
  implementation 'org.apache.poi:poi:5.2.5'
  implementation 'org.apache.poi:poi-ooxml:5.2.5'
  implementation 'org.apache.xmlbeans:xmlbeans:5.2.1'
  implementation 'javax.xml.stream:stax-api:1.0-2'
  implementation 'com.fasterxml:aalto-xml:1.3.3'
}

When

To use Apache POI on Android there
Android app does not allow awt package.
since we can't use these classes on Android. 
Code is took from Apache Harmony, Apache Commons Imaging and witwall/appengine-awt.
