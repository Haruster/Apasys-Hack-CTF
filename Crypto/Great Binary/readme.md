- 오늘은 HackCTF의 Crypto부분 문제인 Great Binary에 대해서 풀어보도록 하겠습니다.

![](https://images.velog.io/images/dsph9245/post/6c925656-82bb-4471-92ca-f96cc78cc9bf/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.27.55.png)

- 일단 문제 파일을 다운로드 해주고 압축을 풀어줍니다. (txt파일이 나왔네요)

![](https://images.velog.io/images/dsph9245/post/441ad9fe-9ffc-47ac-8749-920d0de10949/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.29.22.png)

- hoooo.txt파일을 열어줍니다.

- 그럼 다음과 같은 바이너리 값들이 출력되는 것을 볼 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/51da0218-e96d-4122-977f-c5e7fcbc447e/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.53.47.png)

- 밑의 사이트를 이용해서 해당 바이너리 값들을 문자열(String)값으로 변환해주겠습니다.
http://string-functions.com/binary-string.aspx

- 변환을 해주고 나면 다음과 같은 플래그를 얻을 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/62d66972-22d3-4194-b899-d28f6250662b/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.56.49.png) 

- 해당 플래그를 문제 서버에 제출하면?

![](https://images.velog.io/images/dsph9245/post/dc80c581-f548-4e09-859f-136860afde7b/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.57.45.png)

- 플래그를 얻을 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/f031655a-4fcb-4127-ad70-bd37e86e7066/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%2012.58.05.png)
