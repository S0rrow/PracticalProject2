GridLayout & Notification
========
그리드레이아웃(GridLayout)이란 격자형식으로 데이터나 라벨, 버튼등을 배치하기 위한 레이아웃을 의미한다.
자바에서 gui를 다루면서 좀 써보기는 했는데 안드로이드 스튜디오로 쓰기는 처음이다...
그래서 이왕 쓰는김에 간단하게 그리드레이아웃을 다루면서 노티피케이션을 같이 써보기로 했다.


Apply?
=======
그리드레이아웃으로 버튼을 3행 3열로 배치하고 해당 버튼에 1~9까지의 숫자를 넣어 버튼을 클릭하면 숫자를 텍스트로 알림을 보내는 앱을 짜보려고 한다.


리니어레이아웃 위에, 그리드레이아웃을 배치하고 각 버튼들을 button1, button2, button3, ... button9까지 아이디를 주어서 배치했다.
버튼들의 텍스트는 간단하게 숫자로 해놓았다.

![pp2_GridLayout1](https://github.com/S0rrow/PracticalProject2/blob/master/blog/androidstudio.PNG)

그리드 레이아웃으로 간단하게 버튼들을 배치했으니, 이제 각 버튼들에 Notification을 걸어줄 차례다.

![pp2_oncreate](https://github.com/S0rrow/PracticalProject2/blob/master/blog/oncreate.PNG)

해당 코드는 onCreate 메서드이다. 미리 Button들을 담기 위한 Vector<Button> buttonList를 생성해서 해당 벡터에 버튼들을 저장한다.
그 후, 순서대로 각 버튼에 OnclickListener를 삽입해 한번 클릭하면 createNotification 메서드가, 두번 클릭하면 removeNotification 메서드가 실행되게 했다.

![pp2_createremovenot](https://github.com/S0rrow/PracticalProject2/blob/master/blog/createremovenot.PNG)

createNotification 메서드는 제목을 button num, 내용을 버튼의 숫자로 해서 notification을 만들기 위한 메서드다.
Notification이 생성될때, 특정 id 값을 가지고 생성되게 되는데, 이때 id 값을 각 버튼의 숫자로 했다.

removeNotification 메서드는 특정 버튼이 눌렸을때, 숫자를 받아 그 id값의 notification을 제거하는 메서드다.
    
    
