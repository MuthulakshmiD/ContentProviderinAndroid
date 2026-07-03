
# Ex.No:3 Create Your Own Content Providers to get Contacts details.


## AIM:

To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min. required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “ex.no.3″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the text create your own content providers to get contacts details.
Developed by: Muthulakshmi D
Registeration Number : 212223040122
*/
```


MainActivity.java
```
package com.example.contacts;

import android.database.Cursor;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    TextView textView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        textView = findViewById(R.id.textView);

        StringBuilder builder = new StringBuilder();

        Cursor cursor = getContentResolver().query(
                ContactsContract.CommonDataKinds.Phone.CONTENT_URI,
                null, null, null, null
        );

        if (cursor != null) {
            while (cursor.moveToNext()) {

                String name = cursor.getString(
                        cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));

                String number = cursor.getString(
                        cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));

                builder.append(name)
                        .append(" - ")
                        .append(number)
                        .append("\n");
            }
            cursor.close();
        }

        textView.setText(builder.toString());
    }
}
```
activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="16dp"
        android:textSize="16sp"
        android:text="Contacts will appear here" />

</ScrollView>
```
AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission android:name="android.permission.READ_CONTACTS" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.AppCompat.Light.NoActionBar">

        <activity
            android:name=".MainActivity"
            android:exported="true">

            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

        </activity>
  
    </application>

</manifest>
```

## OUTPUT

<img width="1919" height="1021" alt="Screenshot 2026-05-19 144531" src="https://github.com/user-attachments/assets/a006c764-10fd-4e53-a164-06c0916bddcb" />

<img width="1919" height="1019" alt="Screenshot 2026-05-19 144544" src="https://github.com/user-attachments/assets/00f1f6fa-f41e-4e91-a286-93c82aadbe3e" />

###### call logs
<img width="1919" height="344" alt="Screenshot 2026-05-19 1449121" src="https://github.com/user-attachments/assets/ca4f5652-5129-4d25-b7b4-1021ba5fc14b" />



## RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
