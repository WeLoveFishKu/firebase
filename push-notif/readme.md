## Set Up service Firebase Cloud Messaging
#### 1. Create Package : service
#### 2. Create file/class : MyFirebaseMessagingService
#### 3. in file MyFirebaseMessagingService extend FirebaseMessagingService
    - class MyFirebaseMessagingService : MyFirebaseMessagingService () {}

#### 4. copy code in below on package `**manifest>>androidmanifest.xml**`
```sh
<service
    android:name=".service.MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

#### 5. copy code in below to file MyFirebaseMessagingService


```sh
import android.app.PendingIntent 
import android.content.Intent
import android.util.Log
import androidx.core.app.NotificationCompat
import androidx.core.app.NotificationManagerCompat
import com.example.myfirstapplication.MainActivity
import com.example.myfirstapplication.R
import com.google.firebase.iid.FirebaseInstanceId 
import com.google.firebase.messaging.FirebaseMessagingService
import com.google.firebase.messaging.RemoteMessage

class MyFirebaseMessagingService: FirebaseMessagingService() {
    override fun onNewToken (p0: String) {
    super.onNewToken(p0)
    val refreshToken = FirebaseInstanceId.getInstance().teken
    Log.e( "refreshtoken", refreshToken)

//Kirim si token ke server

}
override fun onMessageReceived(p0: RemoteMessage) {
    super.onMessageReceived(p0)

    //Munculkan notifikasinya
    showNotification (p0.notification?.title.toString(), p0.notification?.body.toString())
}

    fun showNotification (title: String, message: String) {
        val builder = NotificationCompat.Builder(this, "test-notif")
            .setContentTitle(title)
            .setContentText(message)
        val manager = NotificationManagerCompat.from(this)
        manager.notify(222, builder.build())
```

**Then Run Application**
and **Create Campaign on Console Firebase**