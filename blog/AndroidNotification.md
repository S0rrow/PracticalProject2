Android Notitification
========
Android Studio를 통해 사용하는 Notification알림을 생성하는 예제는 이전에 했다.
추가로 실질적으로 구현하기 위해  알아야할 클래스 정보나 필수 메서드에 대해 정리하려고 한다.

기본적으로 알림은 애플리케이션의 ui외부에서 사용자에게 정보를 표시해주는 메시지이다.

Generating Notification
========
Notification 알림을 생성하기 위해서는 기본적으로 NotificationCompat.Builder라는 객체를 사용한다.
해당 객체를 통해 알림의 내용과, 어느 채널을 통해 알림을 표시할지를 정할 수 있다.

Builder객체에는 필수적으로 값을 넣어 선언해야 하는 메소드들이 있다.
- setSmallIcon() // 어느 아이콘을 사용할지를 설정한다.
- setContentTitle() // 어느 제목으로 알림을 표시할지를 설정한다.
- setContentText() // 어느 세부 내용을 가지고 알림을 표시할지를 설정한다.

Showing Notification
========
알림을 표시하기위해서는 NotificationManager라는 객체를 사용하게 된다.
해당 객체의 NotificationManager.notify() 메서드를 호출한다.

이때, 각 알림마다 가지는 고유한 int값을 정의해 고유 id와 Builder객체의 빌드 결과를 패러미터로 반환해 호출하게 된다.

최대한 간단하게 구현한 코드이다.

![pp2_simple_noti](https://github.com/S0rrow/PracticalProject2/blob/master/blog/simplenotification_xml.PNG)


public class MainActivity extends AppCompatActivity {

    private Button create;
    private Button remove;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        create = findViewById(R.id.create);
        remove = findViewById(R.id.remove);

        create.setOnClickListener(new View.OnClickListener() {
            @RequiresApi(api = Build.VERSION_CODES.JELLY_BEAN)
            @Override
            public void onClick(View view) {

                createNotification();
            }
        });

        remove.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                removeNotification();
            }
        });
    }

    private void createNotification() {
        NotificationCompat.Builder builder = new NotificationCompat.Builder(this, "default");

        builder.setSmallIcon(R.mipmap.ic_launcher);
        builder.setContentTitle("Notification Title");
        builder.setContentText("Notification Text");

        builder.setColor(Color.RED);
        builder.setAutoCancel(true);

        NotificationManager notificationManager = (NotificationManager) this.getSystemService(Context.NOTIFICATION_SERVICE);
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            notificationManager.createNotificationChannel(new NotificationChannel("default", "default channel", NotificationManager.IMPORTANCE_DEFAULT));
        }

        notificationManager.notify(1, builder.build());
    }

    private void removeNotification() {
        NotificationManagerCompat.from(this).cancel(1);
    }
}

![pp2simplenotiexe](https://github.com/S0rrow/PracticalProject2/blob/master/blog/simple_noti_execution.PNG)
