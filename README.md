# README_20213002

*오픈소스SW개론(01) - 전찬준 교수님*

*20213002 컴퓨터공학과 김가윤*

***

# 1. Linux 명령어 (top, ps, jobs, kill)
- ## 1.1. top (table of processes)
  top(table of processes)은 실시간으로 CPU 사용률을 보여준다. 
  
  얼마나 많은 처리량과 메모리가 사용되는지, 실행 중인 프로세스에 관한 기타 정보도 보여준다.
  
  3초 간격으로 업데이트 되며 옵션이 없을 시 CPU 사용률 순서로 정렬됨.
  
  사용법 : $ top [option]    *\*빠져나가는 방법 : Ctrl+C, q 등*
  
  - **옵션(option)**
  
  |옵션|내용|
  |:---:|:---:|
  |-b|배치모드로 정보를 출력. 실시간 상화 대화형 모드로 정보를 화면에 일렬로 출력|
  |-d dealy|지정한 시간(dealy 초)의 간격으로 정보를 업데이트하여 출력|
  |-i idle|토글 값이 off일 때, idle 프로세스나 좀비 프로세스 정보를 출력하지 않음|
  |-n num|지정한 시간(num)만큼 업데이트 정보를 출력|
  |-p pid|지정한 프로세스 ID(pid)의 정보만 출력|
  |-q|시간의 간격 없이 계속하여 업데이트 정보를 출력|
  |-s|몇 개의 대화식 명령을 비활성화|
  |-S|누적된 정보 출력|
  
  *top 명령어 실행 후 'h'키 입력시 사용할 수 있는 단축키 목록을 확인 할 수 있음.*
  
  
  
     ![image](https://user-images.githubusercontent.com/106478413/171334889-5c91d0a1-167d-4557-9207-e5b150962b7b.png)
   
     *▲ 터미널에 top 명령어 실행시 뜨는 화면*
     
     - 첫번째 줄 (서버 정보)

        ![image](https://user-images.githubusercontent.com/106478413/171388872-b546a5d4-b87e-4c51-8103-8c05110bbbc7.png)
        
           - top - 14:33:57 : 14시 33분 57초 현재 서버의 시간
           - up : 가동 중
           - 30 min : 30분 째
           - 0 users : 0명의 사용자가 접속
           - load average: 0.05, 0.02, 0.00 : 부하율, 차례대로 1분, 5분, 15분 간의 평균 실행/대기중인 프로세스의 수
         
     - 두번째 줄 (프로세스 정보)

        ![image](https://user-images.githubusercontent.com/106478413/171388983-1a2adbbb-3da3-4956-afe5-ff0a85031f2e.png)

           - total : 전체 가동 중인 프로세스 수
           - running : 실행 중인 프로세스 수
           - sleeping : 대기 중인 프로세스 수
           - stopped : 멈춘 프로세스 수
           - zomibie : 좀비 상태인 프로세스 수
   
     - 세번째 줄 (CPU 정보)

        ![image](https://user-images.githubusercontent.com/106478413/171389139-e3de0286-0347-46dd-acd6-bc3bd9a9ab32.png)

           - us : 유저 레벨에서 사용하고 있는 CPU 비중
           - sy : 시스템 레벨에서 사용하고 있는 CPU 비중
           - ni : nice 정책에 의해 사용중인 CPU 사용률
           - id : 유휴 상태의 CPU 비중
           - wa : 시스템이 I/O 요청을 처리하지 못한 상태에서의 CPU idle 상태인 비중
           - hi : IRQs에 사용된 CPU 사용률
           - si : softIRQs에 사용된 CPU 사용률
           - st : CPU Steal 되어진 값을 의미
      
     - 네번째 줄 (메모리 정보 - MiB MeM)
  
        ![image](https://user-images.githubusercontent.com/106478413/171389264-89a35a21-2f2f-4f9e-97b5-a3022b1716ec.png)

           - total : 전체 물리적인 메모리
           - free : 사용되지 않은 여유 메모리
           - used : 사용 중인 메모리
           - buff/cache : 버퍼된 메모리
     
     - 다섯번째 줄 (메모리 정보 - MiB Swap)
     
        ![image](https://user-images.githubusercontent.com/106478413/171389383-1c4cc952-500d-4f5c-bc83-8e8d975ebe35.png)

           - total : 전체 스왑 메모리
           - free : 사용되지 않은 여유 스왑 메모리
           - used : 사용 중인 스왑 메모리
           - avail Mem : 캐싱 메모리

     - 프로세스 정보
        
        ![image](https://user-images.githubusercontent.com/106478413/171388500-5bc4b937-d422-4ebd-b6b4-48dee15ec210.png)

           - PID : 프로세스 ID
           - USER : 프로세스를 실행시킨 사용자 ID
           - PR : 프로세스의 우선순위 (priority)
           - NI : NICE값. 일의 nice value값. (마이너스 값이면 우선순위가 높다.)
           - VIRT : 가상 메모리의 사용량 (SWAP+RES)
           - RES : 현재 페이지가 상주하고 있는 크기 (Resident Size)
           - SHR : 분할된 페이지, 프로세스에 의해 사용된 메모리를 나눈 메모리의 총합
           - S : 프로세스의 상태 <S(sleeping), R(running), W(swapped out process), Z(zombie)>
           - %CPU : 프로세스가 사용하는 CPU의 사용률
           - %MEM : 프로세스가 사용하는 메모리의 사용률
           - TIME+ : 
           - COMMAND : 실행된 명령어
 
 
 
 
- ## 1.2. ps
  ps(process status)는 현재 실행중인 프로세스의 목록과 상태를 보는 명령어이다.
  
  사용법 : $ ps [option]
  
  - **옵션(option)**
  
  |옵션|내용|
  |:---:|:---:|
  |-e, -A|모든 프로세스를 보여줌|
  |-a|세션 리더와 터미널과 연관된 프로세스들을 제외한 모든 프로세스를 보여줌|
  |-d|세션 리더를 제외한 모든 프로세스를 보여줌|
  |-f|full format으로 세션의 정보를 표시함|
  |-ef|-e와 -f의 옵션 조합. 모든 프로세스를 full format으로 보여줌|
  
  ![image](https://user-images.githubusercontent.com/106478413/171409196-d4dc5b3b-2468-41b6-a55b-3de030cc1c35.png)

  *▲ ps -ef 한 화면*
  
      - UID : 프로세스를 실행한 사람 (User ID)
      - PID : 프로세스를 구분하기 위해 만들어진 프로세스 ID (Process ID)
      - PPID : 부모 프로세스 ID (Parent Prcess ID)
      - C : 스케쥴링을 위한 CPU 사용량
      - STIME : 프로세스 시작 시간
      - TTY : 장치 번호, 해당 프로세스의 입룰력 담당 터미널
      - TIME : CPU 점유 시간
      - CMD : command


- ## 1.3. jobs
  jobs는 작업이 중지된 상태, 백그라운드로 진행 중인 상태 등을 표시하는 명령어 이다.
  
  사용법 : $ jobs [option] [job ID]
  
  - **옵션**
  
  |옵션|내용|
  |:---:|:---:|
  |-l|프로세스 ID를 추가로 출력|
  |-p|각 프로세스 ID에 대해 한 행씩 출력|
  
- ## 1.4. kill
  프로세스에 특정한 signal을 보내는 명령어 이다. 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.
  
  사용법 : $ kill [option or signal] PID
  
  - **signal list ( $ kill -l )**
  
  ![image](https://user-images.githubusercontent.com/106478413/171406416-97f4ab7d-196b-478f-85ba-c9f8ec6c6d27.png)

  *▲ signal list*
  
  - **자주 쓰는 signal**
  
  
  |signal|내용|
  |:---:|:---:|
  |1) SIGHUP|세션이 종료될 때 시스템이 내리는 시그널|
  |2) SIGINT|Ctrl+C, 종료 요청 시그널|
  |9) SIGKILL|강제 종료 시그널|
  |20) SIGSTP|Ctrl+Z, 일시 중지 요청 시그널|
  
  **프로세스를 안전하게 종료시키려면 SIGKILL을 이용한 종료는 가급적 사용하지 않는 것이 좋다.**
***

# 2. Linux vim 에디터 매크로 활용 방법

- **기본 형태 : q[Name][Commands]q**

1) q<Name> : [Name]이라는 이름의 매크로를 시작한다.     
      *\* 이 때 [Name]에는 알파벳 하나를 사용함. (a~z)*

2) 매크로로 만들 명령어(Commands) 입력

3) 명령 모드에서 q : 매크로를 저장한다.

4) @[Name] : [Name]이라는 이름의 매크로를 (1회) 실행한다. 
   - [Number]@[Name] : [Number]만큼의 매크로를 실행함.
   - @@ : 가장 최근 재생된 매크로가 재생됨.

  ex) 모든 행을 주석 처리하는 매크로 qai//<ESC>+q
  
  - qa를 눌렀을 때 화면
  
  ![image](https://user-images.githubusercontent.com/106478413/171400086-78520ecb-0c22-4562-96f2-ded94603fa2a.png)
  
  - 명령어 입력 i//<ESC>+ 하고 종료 q 했을 때 화면
  
  ![image](https://user-images.githubusercontent.com/106478413/171401441-d6e6faff-1fd8-4760-b298-b8d485a28577.png)  

  - 매크로 실행하는 화면 (전체 행 주석처리 하기 위하여 3@a 입력)
  
  ![image](https://user-images.githubusercontent.com/106478413/171401728-f0b75577-44e0-43b6-9d04-4a61bacd1a14.png)

  *▲ 모든 행이 주석처리 되었다.*
***
