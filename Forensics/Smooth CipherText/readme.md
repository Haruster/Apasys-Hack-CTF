- 오늘은 HackCTF의 Crypto분야의 문제인 Smooth CipherText를 풀어보도록 하겠습니다.
![](https://images.velog.io/images/dsph9245/post/d2779b47-6320-4168-89fc-f961fa97bad3/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%EC%A0%84%202.24.54.png)

- 문제를 보면 다음과 같은 암호문이 있는 것을 볼 수 있다. 

- 여기서 플래그 값도 암호화가 되어 있는 것을 볼 수 있는데 바로 이 부분입니다.

![](https://images.velog.io/images/dsph9245/post/26370b6c-dcc4-47fa-9f9d-c7a75e496fed/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%204.47.38.png)

- LymoADJ가 바로 HackCTF라고 볼 수 있는데 m과 A 둘다 c를 나타내는 것으로 보아 카이사르 암호는 아니라고 볼 수 있고 해당 암호는 비네제르 암호라는 것을 알 수 있었습니다.

- 카이사르 암호 : 카이사르 암호는 암호화 하고자 하는 내용(평문)을 알파벳별로 일정한 거리만큼 밀어서 다른 알파벳으로 치환하는 방법을 말합니다.

- 비네제르 암호 : https://ko.wikipedia.org/wiki/비즈네르_암호

- 그럼 해당 암호문을 비네제르 디코딩 사이트에 넣어보겠습니다.

- https://www.guballa.de/vigenere-solver

- 위의 사이트를 열어줍니다.
![](https://images.velog.io/images/dsph9245/post/fb97817c-3773-4781-8b47-59fb0b538332/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%204.55.57.png)

- 그 다음에 해당 암호문을 넣어주고 복호화를 진행해줍니다.

![](https://images.velog.io/images/dsph9245/post/53917532-a613-494a-9565-e3a62af2ff41/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%204.56.50.png)

- 그러면 다음과 같이 복호화가 되는데요 자세히 보면 플래그 안의 내용은 제대로 복호화가 이루어지지 않았음을 알 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/6d42eae0-32eb-42fd-83da-d72cdbee5c35/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%204.57.18.png)

- 해당 부분만 따로 복사를 하여 다시 복호화를 진행해주겠습니다.

![](https://images.velog.io/images/dsph9245/post/94902b6d-6ac4-49b4-a919-11b0cc3eb142/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%205.00.07.png)

- 그러면 제대로된 플래그 값이 나오는 것을 확인할 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/4f918be4-1679-4ba0-a836-7b4c4df7b3ba/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%205.01.58.png)

- 이 값을 문제 서버에 제출해주면?

![](https://images.velog.io/images/dsph9245/post/72942ee9-79b2-45ed-aa65-c7fb7563d945/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%205.02.41.png)

- 성공적으로 플래그를 얻을 수 있는 걸 확인할 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/a8651179-5a71-4d63-8fda-73f74e3bc2f2/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-16%20%EC%98%A4%ED%9B%84%205.03.07.png)
