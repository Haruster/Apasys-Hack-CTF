- 오늘은 HackCTF의 Foresic분야의 문제인 Question?을 풀어보도록 하겠습니다.
- 일단 제일 먼저 문제를 본 다음 첨부파일을 다운로드 해줍니다.

![](https://images.velog.io/images/dsph9245/post/4db34fcf-af4a-4b39-9b98-a8a98c679154/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.36.04.png)

- 파일을 다운로드 한 후 보면 문제 파일이 zip으로 압축이 되어 있습니다.

![](https://images.velog.io/images/dsph9245/post/22122304-5748-49a7-a702-554fc323631b/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.28.06.png)

- 압축 프로그램을 사용해서 파일을 열어보면 Do_You_Know_HXD.jpg라는 파일이 있는 것을 볼 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/fc2cf7c6-26b7-4434-b8e7-7053075fc9c6/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.29.43.png)

- 파일을 압축 해제 해줍니다. 그리고나서 HxD로 해당 파일을 열어줍니다.

![](https://images.velog.io/images/dsph9245/post/05523faa-9d1b-4d24-8eff-d44bfd71d190/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.30.07.png)

![](https://images.velog.io/images/dsph9245/post/dbea518e-bd36-4258-a6c9-af935177b5b4/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.30.27.png)

![](https://images.velog.io/images/dsph9245/post/6f81f832-c953-41cb-ad03-640f74256b69/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.30.55.png)

- 파일을 열어보면 다음과 같은 화면이 나옵니다.

![](https://images.velog.io/images/dsph9245/post/233617e7-ba98-4de1-808f-5ba480eb9c1e/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.31.23.png)

- 제일 먼저 Ctrl + f 즉, 찾기를 이용해서 HackCTF문제의 플러그 구문이 있는지 확인해줍니다.

![](https://images.velog.io/images/dsph9245/post/c327b061-0173-4a89-aa44-4ccd9d1fe6fb/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.32.02.png)

- 찾기를 진행하면 해당 문제는 플래그가 그냥 나와있는 걸로 볼 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/35052616-8237-4074-90c5-3ae26687a2e8/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.34.57.png)

- 해당 플래그를 문제 서버에 제출해주면?

![](https://images.velog.io/images/dsph9245/post/4bb61186-9284-4d78-8d64-f31e7550c3b8/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.39.03.png)

- 정상적으로 solve가 되는 것을 볼 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/05bd35c9-e015-49b3-86c0-6dc9b9fe0a32/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%ED%9B%84%207.39.17.png)

