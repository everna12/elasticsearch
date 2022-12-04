# ElasticSearch Twitter logging<br/>
<br/>

## Step1
우선 데이터를 분석하기 위해서 트위터 개발자 계정이 필요하다.<br/>
계발자 계정이 있어야 트위터 플러그인에서 사용하는 API키값을 얻을 수 있다.<br/>
트위터 개발자 계정을 만들고 로그인 한다.<br/>
![Alt text](1.PNG)<br/>
그 후 오른쪽 상단에 Developer portal 링크로 들어간다.
![Alt text](2.PNG)<br/>
키를 얻기 위해서는 앱이 필요하다.<br/>
<br/>
![Alt text](3.PNG)<br/>
사용 용도를 선택해주고<br/>
![Alt text](4.PNG)<br/>
앱 이릅을 정하고 Next 버튼을 누르면<br/>
![Alt text](5.PNG)<br/>
앱이 만들어진것을 확인할 수 있다.<br/>
그리고 화면에 Bearer Token의 Regenerate 버튼을 클릭하면<br/>
![Alt text](6.PNG)<br/>
Bearer Token의 키 값을 받을 수 있다.<br/>



## Step2
![Alt text](7.PNG)<br/>
elasticsearch를 실행해주고,<br/>
![Alt text](8.PNG)<br/>
엘라스틱서치가 완전히 실행되면 키바나를 실행해준다.<br/>
![Alt text](9.PNG)<br/>
엘라스틱 서치와 키바나를 준비하는 동안 로그스태시
<br/>

## Step3

키바나가 완전히 실행되면 logstash파일에 들어가서 이번에는 실행하는 것이 아닌 경로부분에 cmd를 입력하여 커맨드 창을 실행한다.<br/>

커맨드창을 실행 후 bin\logstash.bat =f config\logstash-twitter.conf 명령어를 입력한다.<br>

위 그림은 명령어를 입력한 후 실행장면이다.
<br/>

## Step4
![Alt text](8.PNG)<br/>
미리 준비한 tweetlog > 가상환경 폴더이다. 가상환경 폴더에서 logstash처럼 경로 부분에 cmd를 입력하여 커맨드 창을 실행한다.<br/>
커맨드창을 실행후 Scripts\activate 명령어를 입력하여 가상화 모드에 진입한다.<br/>
![Alt text](9.PNG)<br/>
위 그림은 가상화 모드에 진입한 상황이다.<br/>
![Alt text](10.PNG)<br/>
가상화모드에 python이 설치되어 있는지 확인하기 위해 python 명령어를 입력하여 확인한다. (확인 후 나가는 명령어는 quit()이다.)<br/>
![Alt text](11.PNG)<br/>
가상화 모드에 pip install tweepy를 입력하여 설치를 진행한다.<br/>
![Alt text](12.PNG)<br/>
가상화 모드에 pip install python-logstash를 입력하여 설치를 진행한다. <br/>

## Step5
![Alt text](13.png)<br/>
위 py파일은 트위터를 로깅하기위해 준비한 파일이다. 인터넷에 올릴때는 외부인이 악용할 우려가 있는 토큰은 꼭 가려주도록 한다.<br/>
![Alt text](14.png)<br/>
아까 준비해둔 가상화 환경에서 python tweepy2.py 명령어를 입력하여 파일을 실행한다. (py파일은 가상화 폴더 안에 같이 있는 것이 실행하기에 편하다.)<br/>
![Alt text](15.png)<br/>
아까 키바나에서 bin\logstash.bat =f config\logstash-twitter.conf 명령어를 실행했던 화면에 트위터가 로깅되는 것을 확인 할 수 있다.<br/>
충분한 시간동안 로그를 수집하면된다.<br/>

## Step6
![Alt text](16.png)<br/>
엘라스틱 서치 홈페이지에 접속을한다.(http://localhost:9200/)<br/>
접속후에 엘라스틱 왼쪽상단에 있는 메뉴바를 눌러 맨밑에 Stack Management에 진입한다.<br/>
![Alt text](17.png)<br/>
Stack Management에 진입 후 좌측 Index Patterns를 누르고 우측 상단Create index pattern을 누른다.<br/>
![Alt text](18.png)<br/>
Create index pattern을 진행한 후에 index pattern name 아래에 미리 py 파일에서 설정한 이름을 검색후에 Next step을 눌러 진행한다.<br/>
![Alt text](19.png)<br/>
좌측 상단 메뉴바를 눌러 Discover에 들어간 후 좌측에서 설정한 이름을 선택한 후에 우측 상단 트위터 로그를 수집한 시간을 설정한다. 그러면 각 시간마다. 트위터 로그가 수집된 내역과 시간별 수집된 로그양을 보여준다.<br/>

위 처럼 어렵지 않게 트위터 로그를 수집할 수 있다.
