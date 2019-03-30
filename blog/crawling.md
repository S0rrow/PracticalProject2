Crawling is?
==============
__크롤링__이란 웹 서버에서 데이터를 받아와 필요한 내용을 추출해 사용하는 기법을 의미한다.
파싱(Parsing)을 통해 특정 데이터에서 일정한 패턴이나 순서를 가지는 데이터를 분리해 묶는 것을 기반으로 한다.

Java에서 크롤링은 Jsoup이나 Selenium같은 외부 라이브러리를 통해 이루어진다.
- Jsoup: 특정 url에서 데이터를 받아오고 그 데이터를 파싱하는데 사용.
- Selenium: 가상으로 브라우저를 생성해 유저가 직접 행동하는 것처럼 웹을 사용, 데이터를 받을 수 있게 함.

Jsoup
==============
Jsoup 라이브러리의 주요 사용방식들에 대해 정리했다.
1. connect()라는 메서드를 통해 url이 주어질때 그 url에 접속한다.
2. get() 메서드를 통해 웹 서버가 페이지의 정보를 보내올때, HTML형식으로 그 페이지의 소스를 받아온다.
3. 받아온 페이지의 소스를 Document, Element 등의 객체로 파싱한다.

단 Jsoup 라이브러리만으로는 페이지의 소스만을 가져오기 때문에 실제 브라우저에서 해석하는 코드를 가져오지는 못한다.

이때문에 Selenium 라이브러리를 사용하게 된다.


![pp2source](https://github.com/S0rrow/PracticalProject2/blob/master/blog/pp2source.PNG)

해당 코드는 루리웹(https://bbs.ruliweb.com/)의 오른쪽 베스트를 리스트로 콘솔창에 보여주는 간단한 코드이다.
오른쪽 베스트에 해당하는 태그가 ul이고, 클래스가 right_best_list이므로 해당하는 태그와 클래스를 넣어 select()함수로 HTML내에서 분리해준다.
분리된 데이터에서 필요로 하는것은 단순히 제목뿐이므로 제목과 링크를 담은 li 태그에서 다시 제목이 저장된 a 태그에서 텍스트만 분리해서 콘솔창에 출력해준다.
해당 코드의 실행결과는 다음과 같다.

![pp2](https://github.com/S0rrow/PracticalProject2/blob/master/blog/pp2hw1text.PNG)
