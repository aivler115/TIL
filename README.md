2024-09-20

오늘 배웠던 것들 중에서 헷갈렸던 부분 그리고 느낀 점을 정리해보려고 합니다

​

1. get과 post는 둘 다 보내다의 느낌인데...?

HTTP method는 여러가지가 있지만 get과 post를 처음 접했을 때의 어려움이 아직도 기억에 납니다. 개념이 헷갈려 method 방식을 post로 해놓고 parameter로 입력값을 받았던 실수가 있었습니다. 분명 단어 자체로는 GET은 '다가가 얻다', POST는 '멀리 보내다'라는 느낌인데 아직도 웹프레임워크에서 둘 다 '보내다'의 느낌이 강하게 듭니다. 

이번 강의를 통해 둘의 가장 큰 차이는 GET는 데이터 노출, POST는 데이터 비노출이라고 합니다.

​

GET : https://mail.naver.com/all?page={page_number}처럼 page_number를 사용자가 버튼을 눌러 변하게 하든 또는 직접 url를 변경하여 엔터를 눌러 'URL을 보내고 페이지 정보를 얻습니다'

POST : 로그인 화면에서 id와 password 창에 입력 후 '로그인 버튼'을 눌러 HTTP의 Body에 Query를 포함하여 다양한 정보({id:1, password:abc})를 서버에 보내면 '로그인 상태를 위한 정보'를 얻습니다.

​

1. Cookie, Session, Cache는 비슷하면서도 다르구나

Cookie(쿠키)

=> 클라이언트(브라우저)에 저장되는 작은 데이터 (로그인 정보)


Cookie(쿠키)

 Session(세션)

=> 클라이언트(브라우저)와 서버 간의 일시적인 상호작용 상태를 위한 데이터(로그인 상태 유지)


Session(세션)

Cache(캐시)

=> 클라이언트, 서버의 RAM(메모리)에 저장하는 자주 사용되는 데이터


Cache(캐시)

​

2. return 뒤에는 객체가 와야 하는구나...

파이썬을 처음 배웠을 때 return의 개념이 모호해서 반환의 이미지만 가지고 있었습니다.

그래서 지금도 종종 실수를 하곤 합니다. 그래서 이번 기회에 다시 정리하고자 합니다.

return은 객체를 함수 바깥으로 내보내는 역할이다.

def my_function():
    a = pd.DataFrame()  # 먼저 변수에 할당
    return a            # 그 변수를 반환
return 뒤에 변수 할당 명령어를 쓸 수 없다

def my_function():
    return a = pd.DataFrame()  # 할당된 a는 반환이 안 된다
​

3. 클래스는 사용자 정의된 데이터 타입임을 잊지 말자

# 클래스 선언
class Animal:
    sound = []
    def dog(self, feature):
        self.sound = feature
    def cat(self, feature):
        self.sound = feature

# 변수 선언
a = Animal()
b = Animal()

print(a.sound)  # []
print(b.sound)  # []

# 메서드 실행
a.dog('멍멍') # feature = '멍멍'
b.cat('야옹')

print(a.sound) # 멍멍 # self.sound 호출
print(b.sound) # 야옹

print(type(a))  # <class 'user_code.Animal'>
클래스를 변수에 할당하니 변수 자체가 클래스가 됩니다

클래스가 가진 모든 함수(메서드)를 변수가 쓸 수 있게 됩니다.

​

4. __init__(self, x)는 x의 초기값 설정을 위한 특별한 메서드이다

# 클래스 선언
class Animal:
    def __init__(self, sound): # __init__으로 변수 선언 시 sound의 초기값 설정이 필수가 된다
        self.sound = sound
    def dog(self, feature):
        self.sound = feature
    def cat(self, feature):
        self.sound = feature

# 변수 선언
# '멍' 미입력시 TypeError: Animal.__init__() missing 1 required positional argument: 'sound'
a = Animal('멍')
b = Animal('옹')

print(a.sound)  # 멍
print(b.sound)  # 옹

# 메서드 실행
a.dog('멍멍')
b.cat('야옹')

print(a.sound) # 멍멍
print(b.sound) # 야옹
​

5. (결론) 전체적인 그림을 보기 위해서 필요한 지식일 것 같습니다

아무것도 모른 채 바로 서비스 구현하는 것과 지금처럼 기초적인 문법과 학문적인 개념을 배우고 나서 서비스를 구현하는 것을 비교하면 후자가 완성도나 깊이가 더 있을 것 같습니다.

​

하지만 만약 제가 후자처럼 했다면 질려서 프로그래밍 공부를 포기했을 것 같다는 생각이 들곤 하네요... 만들고 싶은 것을 정하고 기능 구현을 위해 공부할 때가 더 재밌었고 기억에 잘 남았던 것 같습니다. 물론 완성 퀄리티는 매우 떨어져서 아쉬웠던 경험이긴 했지만요 :D
