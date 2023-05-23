# 리눅스 명령어에 대해 조사해보자!
리눅스 운영 체제에서 **'top'** 은 시스템 상태를 모니터링하고 현재 실행 중인 프로세스를 
실시간으로 관찰하는 명령어입니다. **'top'** 을 실행하면 터미널 창에 다양한 정보가 표시된다.
메모리 사용량, CPU 사용량 등을 나타내주며 **'top'** 를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여준다. 위에는 전체의 요약이 있으며 아래에는 각 프로세스마다 구체적인 내용을 포함하고 있다.
요약 영역은 **'top'** 에서 상단에 위치하고 있다.
요약 영역에 나타나는 대표적인 값은 시간, 유저, load average, 테스크, cpu, 메모리를 나타낸다. 


* ### top 명령어 실행 화면
![top 실행 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/78db63c7-ec0a-446a-b759-cbe997727dab)
## 요약 영역
![top 요약 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/36d1b835-b116-45fc-8406-7bc8d81ada76)

* ### 시스템 현재 시간
실행화면의 상단을 보면 시스템 현재 시간, OS가 살아있는 시간, 그리고 유저의 세션수가 표시되는 영역이 있습니다. 가장 먼저 보이는 숫자가 시스템의 현재 시간이다. 다음으로 표시되는 것이 OS가 얼마나 살아있는 지 나타낸다. days와 시간으로 표시되며 실행 화면에선 171days와 2시간 17분동안 서버가 살아있었다는 것을 알 수 있다.

* ### 유저 세션
X users 로 나타나는 것이 현재 접속중인 유저 세션 수이다.
자세한 유저세션은 'who' 명령어를 통해 알 수 있다.
'who' 명령어 실행 결과는 다음과 같다.
* ### Load average
2번째 영역은 로드 애버리지 영역입니다. 해당 영역은 CPU Load의 이동 평균를 표시합니다. 앞에서 부터 1분, 5분, 그리고 15분에 대한 평균값입니다. CPU Load란 CPU가 수행하는 작업의 양 입니다. 리눅스에서는 실행되거나 대기중인 프로세스의 평균입니다. 싱글 코어일 경우 1.0의 값이 CPU 100%를 사용하고 있다는 의미입니다. 멀티 코어라면 해당 코어수 만큼 * N을 한 값이 CPU 100%를 사용한다는 의미가 됩니다. 만약 100%를 넘어간다면 CPU에서 처리하지 못하고 대기하고 중인 프로세스가 있다고 보시면됩니다.
* ### Tasks
2번째 줄에는 Tasks에 관한 내용이 출력됩니다. Tasks는 현재 프로세스들의 상태를 나태내주는 영역입니다. Total은 전체 프로세스, running은 running 상태인 프로세스, sleeping은 대기상태인 process, stopped는 종료된 프로세스, zombies는 좀비상태인 프로세스의 수를 나타냅니다.
* ### CPU
Tasks 아래 %Cpu(s)라는 영역이 있습니다. 이 영역은 CPU가 어떻게 사용되고 있는지 그 사용율을 보여주는 영역입니다. 모든 값의 총 합은 100% 이며 이를 퍼센테이지로 나누어서 보여줍니다. 각 요소는 아래와 같습니다.

- us : 프로세스의 유저 영역에서의 CPU 사용률
- sy : 프로세스의 커널 영역에서의 CPU 사용률
- ni : 프로세스의 우선순위(priority) 설정에 사용하는 CPU 사용률
- id : 사용하고 있지 않는 비율
- wa : IO가 완료될때까지 기다리고 있는 CPU 비율
- hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
- si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
- st : CPU를 VM에서 사용하여 대기하는 CPU 비율
* ### 메모리
%Cpu(s) 영역 아래에 메모리와 관련된 영역이 있습니다. 첫번째 줄은 RAM의 메모리 영역으로 Mem이라 표시되어있는 부분입니다. 그리고 아랫줄은 디스크를 메모리 처럼 이용하는 Swap 메모리 영역입니다. 일반적으로 Mem의 사용량이 거의 가득 찼을때 Swap 메모리 영역을 사용합니다. 이 영역은 디스크이기 때문에 RAM 메모리보다 속도가 많이 느린 단점을 가집니다.

- total : 총 메모리 양
- free : 사용가능한 메모리 양
- used : 사용중인 메모리 양
