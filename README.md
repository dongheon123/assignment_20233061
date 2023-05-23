# 리눅스 명령어에 대해 조사해보자!
---
## 명령어 **top**



리눅스 운영 체제에서 **'top'** 은 시스템 상태를 모니터링하고 현재 실행 중인 프로세스를 
실시간으로 관찰하는 명령어이다. **'top'** 을 실행하면 터미널 창에 다양한 정보가 표시된다.
메모리 사용량, CPU 사용량 등을 나타내주며 **'top'** 를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여준다. 상단에는 전체의 요약이 있으며 하단에는 각 프로세스마다 구체적인 내용을 포함하고 있다.
요약 영역은 **'top'** 에서 상단에 위치하고 있다.
요약 영역에 나타나는 대표적인 값은 시간, 유저, load average, tasks, cpu, 메모리를 나타낸다. 

### 사용법

**$ top**

### top 명령어 실행 화면
![top 실행 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/78db63c7-ec0a-446a-b759-cbe997727dab)
### 요약 영역
![top 요약 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/36d1b835-b116-45fc-8406-7bc8d81ada76)

* ### 시스템 현재 시간
실행화면의 상단을 보면 시스템 현재 시간, OS가 살아있는 시간, 그리고 유저의 세션수가 표시되는 영역이 있습니다. 가장 먼저 보이는 숫자가 시스템의 현재 시간이다. 다음으로 표시되는 것이 OS가 얼마나 살아있는 지 나타낸다. days와 시간으로 표시되며 실행 화면에선 171days와 2시간 17분동안 서버가 살아있었다는 것을 알 수 있다.

* ### 유저 세션
3 users 로 나타나는 것이 현재 접속중인 유저 세션 수이다.
실행 화면에서 현재 3명의 유저가 현재 접속중이라는 것을 의미한다.
자세한 유저세션은 'who' 명령어를 통해 알 수 있다.
'who' 명령어 실행 결과는 다음과 같다.
![who 실행 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/be02c745-c759-4edb-8236-282fc3acb1cd)

* ### Load average
2번째 영역은 로드 애버리지 영역이다. 해당 영역은 CPU Load의 이동 평균를 표시한다. 앞에서 부터 1분, 5분, 그리고 15분에 대한 평균값입니다. CPU Load란 CPU가 수행하는 작업의 양 이다. 리눅스에서는 실행되거나 대기중인 프로세스의 평균이다. 싱글 코어일 경우 1.0의 값이 CPU 100%를 사용하고 있다는 의미d이. 멀티 코어라면 해당 코어수 만큼 * N을 한 값이 CPU 100%를 사용한다는 의미가 된다. 만약 100%를 넘어간다면 CPU에서 처리하지 못하고 대기하고 중인 프로세스가 있다고 보면 된다.
* ### Tasks
2번째 줄에는 Tasks에 관한 내용이 출력된다. Tasks는 현재 프로세스들의 상태를 나태내주는 영역이다. Total은 전체 프로세스, running은 running 상태인 프로세스, sleeping은 대기상태인 process, stopped는 종료된 프로세스, zombies는 좀비상태인 프로세스의 수를 나타낸다.
* ### CPU
Tasks 아래 %Cpu(s)라는 영역이 있다. 이 영역은 CPU가 어떻게 사용되고 있는지 그 사용율을 보여주는 영역이다. 모든 값의 총 합은 100% 이며 이를 퍼센테이지로 나누어서 보여준다. 각 요소는 아래와 같다.

- us : 프로세스의 유저 영역에서의 CPU 사용률
- sy : 프로세스의 커널 영역에서의 CPU 사용률
- ni : 프로세스의 우선순위(priority) 설정에 사용하는 CPU 사용률
- id : 사용하고 있지 않는 비율
- wa : IO가 완료될때까지 기다리고 있는 CPU 비율
- hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
- si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
- st : CPU를 VM에서 사용하여 대기하는 CPU 비율
* ### 메모리
%Cpu(s) 영역 아래에 메모리와 관련된 영역이 있다. 첫번째 줄은 RAM의 메모리 영역으로 Mem이라 표시되어있는 부분이다. 그리고 아랫줄은 디스크를 메모리 처럼 이용하는 Swap 메모리 영역이다. 일반적으로 Mem의 사용량이 거의 가득 찼을때 Swap 메모리 영역을 사용한다. 이 영역은 디스크이기 때문에 RAM 메모리보다 속도가 많이 느린 단점을 가진다.
- total : 총 메모리 양
- free : 사용가능한 메모리 양
- used : 사용중인 메모리 양

## 디테일 영역
![top 디테일 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/878e57bf-24de-4cd5-a3e8-a6a6e19349cc)

- **PID**
  - PID는 프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값이다.
  
- **USER**
  - 해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름이다.
  
- **PR & NI**
  - **PR** : 커널에 의해서 스케줄링되는 우선순위이다.
  - **NI** : PR에 영향을 주는 nice라는 값이다.
  
- **VIRT, RES, SHR, %MEM**

   ***해당 필드들은 프로세스의 메모리와 관련있다.***

  - **VIRT** : 프로세스가 소비하고 있는 총 메모리이다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함한다.
  
  - **RES** : RAM에서 사용중인 메모리의 크기를 나타낸다.
  
  - **SHR** : 다른 프로세스와의 공유메모리(Shared Memory)를 나타낸다.
  
  - **%MEM** : RAM에서 RES가 차지하는 비율을 나타낸다.
  
- **S** : 프로세스의 현재 상태를 나타낸다.

- **TIME+** : 프로세스가 사용한 토탈 CPU 시간을 나타낸다.

- **COMMAND** : 해당 프로세스를 실행한 커맨드를 나타낸다.

### top 실행 중의 명령어 옵션
- **SPACE** : 화면을 갱신한다.
- **h, ?** : 도움말을 출력한다.
- **k** : kill 명령을 내린다. PID값을 입력하면 종료신호를 보낸다.
- **i** : Zombi, idle 프로세스의 출력을 on / off 한다.
- **n or #** : 출력한 프로세스의 수를 지정한다.
- **q** : top을 종료한다.
- **r** : Nice 값을 변경한다.
- **s** : 화면을 갱신하는 시간을 변경한다.
- **F, f** : 보여줄 항목을 추가하거나 삭제한다.
- **O, o** : 보여줄 항목의 순서를 바꾼다.
- **I** : top의 맨 윗줄을  on / off 한다.
- **m** : 메모리의 관련된 항목을 on / off 한다.
- **t** : 프로세스와 CPU 항목을 on / off 한다.
- **c** : Command line의 옵션을 on / off 한다.
- **M** : 프로세스의 RSS값을 정렬한다.
- **P** : %CPU 값으로 정렬한다. (기본값)
- **T** : Time 값으로 정렬한다.
- **W** : 바꾼 설정을 저장한다.
---
## 명령어 **ps**

**'ps'** 명령어는 'process status'의 준말로 현재 실행중인 프로세스 목록과 상태를 보여준다.

### 사용법
**$ ps [option]**

### ps 명령어 실행 화면
![ps 명령어 실행 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/9bc8cf24-6909-4792-b374-4c3b95780009)

### 사용 방법 예시

- '$ ps' : 현재 사용자의 실행 중인 프로세스 목록을 보여준다.
- '$ ps -ef' : 모든 사용자의 실행 중인 프로세스 목록을 보여준다.
- '$ ps -e' : 모든 실행 중인 프로세스 목록을 보여준다.
- '$ ps -aux' : 모든 사용자의 실행 중인 프로세스 목록을 자세한 형식으로 보여준다.
- '$ ps -l' : 자세한 형식으로 실행 중인 프로세스 목록을 보여준다.

출력내용은 다음과 같다.
- UID : 프로세스를 실행하는 사용자의 UID이다.
- PID : 프로세스의 고유 식별자이다.
- PPID : 부모 프로세스의 PID이다.
- C : 프로세스의 CPU 사용량이다.
- STIME : 프로세스가 시작된 시간이다.
- TTY : 프로세스가 연결된 터미널 장치이다.
- TIME : 프로세스가 실행된 총 시간이다.
- CMD : 프로세스를 실행하는 명령어 또는 프로그램의 이름이다.

---
## **jobs 명령어**
**'jobs'** 명령어는 백그라운드로 실행중인 프로세스나 현재 중지된 프로세스의 목록을 출력해주는 명령어이다.

### 사용법
**$ jobs [option]**

### jobs 명령어 실행 화면
![jobs 실행 화면](https://github.com/dongheon123/assignment_20233061/assets/113902969/dc2d82d1-f12d-4e7c-b2d4-d525e6d1b501)
[출처] https://veneas.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EC%9E%91%EC%97%85-%EC%A0%84%ED%99%98-Background-Foreground

### jobs로 알 수 있는 세션의 상태값

- 'Running' : 작업이 계속 진행 중임을 뜻한다.
- 'Done' : 작업이 완료되어 0을 반환하고 종료했음을 뜻한다.
- 'Done(code)' : 작업이 정상적으로 완료되었으며 0이 아닌 코드를 반환했음을 뜻한다.
- 'Stopped' : 작업이 일시 중단됨을 뜻한다.
- 'Stopped(SIGTSTP)' : SIGTSTP 시그널이 작업을 일시 중단했음을 뜻한다.
- 'stopped(SIGSTOP)' : SIGSTOP 시그널이 작업을 일시 중단했음을 뜻한다.
- 'stopped(SIGTTIN)' : SIGTTIN 시그널이 작업을 일시 중단했음을 뜻한다.
- 'stopped(SIGTTOU)' : SIGTTOU 시그널이 작업을 일시 중단했음을 뜻한다.

### 사용 방법 예시

- '-l' : 프로세스 그룹 ID를 state 필드 앞에 출력한다.
- '-n' : 프로세스 그룹 중에 대표 프로세스 ID를 출력한다.
- '-p' : 각 프로세스 ID에 대해 한 행씩 출력한다.
- '-s' : 프로세스 중 멈춰있는 프로세스만 출력한다.
- '-r' : 프로세스 중 실행중인 프로세스만 출력한다.
- command : 지정한 명령어를 실행한다.
