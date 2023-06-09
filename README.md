# 리눅스 명령어
## 1. top

### 개념
리눅스 계열 서버의 OS 상태를 확인할 수 있는 CLI 어플레이케이션으로 시스템 프로세스/메모리 사용 현황을 실사간으로 확인한다.

### top 옵션
* -b : 배치모드로 정보를 출력한다. 실시간 상화 대화형모드로 정보를 화면에 일렬로 출력한다.

* -d delay : 지정한 시간(delay 초)의 간격으로 정보를 업데이트하여 출력한다.

* -i idle : 토글값이 off일 때, idle 프로세스나 좀비 프로세스 정보를 출력하지 않는다.

* -n num : 지정한 시간(num)만큼 업데이트 정보를 출력한다.

* -p pid : 지정한 프로세스 ID(pid)의 정보만을 출력한다.

* -q : 시간의 간격 없이 계속하여 업데이트 정보를 출력한다.

* -s : 몇 개의 대화식 명령을 비활성화한다(시큐어 모드).

* -S : 누적된 정보를 출력한다(cumulative 모드).

### top 실행 예제
![image](https://github.com/namoikmn/helloworld/assets/133830049/8cab8fef-5e00-4e9d-85c5-93662d6cc61a)

- 5:05: 5시간 5분 전에 서버 구동

- load average: 현재 시스템이 얼마나 일을 하는지를 나타냄. 3개의 숫자는 1분, 5분, 15분 간의 평균 실행/대기 중인 프로세스의 수. CPU 코어수 보다 적으면 문제 없음 

- Tasks : 프로세스 개수

- KiB Mem, Swap : 각 메모리의 사용량

- PR : 실행 우선순위

- VIRT 

  * 프로세스가 사용하고 있는 virtual memory의 전체 용량
  
  * 프로세스에 할당된 가상 메모리 전체
  
  * SWAP + RES

- RES

  * 현재 프로세스가 사용하고 있는 물리 메모리의 양

  * 실제로 메모리에 올려서 사용하고 있는 물리 메모리

  * 실제로 메모리를 쓰고 있는 RES가 핵심

- SHR
  
  * 다른 프로세스와 공유하고 있는 shared memory의 양
  
  * 예시로 라이브러리를 들 수 있음. 대부분의 리눅스 프로세스는 glibc라는 라이브러리를 참고하기에 이런 라이브러리를 공유 메모리에 올려서 사용
  
- S : 프로세스 상태(작업중, I/O 대기, 유휴 상태 등)

## 2. ps

### 개념
ps(=process status) 줄인말로, 현재 실핸중인 프로세스 목록과 상태를 출력해서 보여주는 기능을 한다.

### ps 옵션
* -A: 모든 프로세스 출력
 
* a: 터미널과 관련된 프로세스 출력, x옵션과 결합하여 사용

* -a: 셰선 리더를 제외하고 데몬 프로세스 처럼 터미널에 종속되지 않는 모든 프로세스 출력

* -e: 커널 프로세스 제외한 모든 프로세스 

* -ef: 표준 문장으로 시스템의 모든 프로세스를 출력

* -f: 풀포멧 보여줌.
 
* -l/l: 긴 포멧을 보여줌.

* -o: 출력 포맷을 지정하는 옵션으로 값으로 pid, tty, time, cmd 등을 지정할 수 있다.

* -M: 64비트 프로세스 보여줌.

* -m: 프로세스 뿐만이 아닌 커널 스레드들도 보여줌.

* -p: 특정 PID 지정시 사용

* -r: 현재 실행중인 프로세서 보여줌.

* u: 프로세스의 소유자를 기준으로 출력

* -u: 특정 사용자의 프로세스 정보 확인시 사용

* x: 데몬 프로세스처럼 터미널에 종속되지 않는 프로세스 출력 

* -x: 로그인 상태에 있는 아직 완료되지 않는 프로세스 

### ps 사용 예시
1. 일반 ps 사용

![image](https://github.com/namoikmn/helloworld/assets/133830049/fe63a64e-d266-43a4-a2ad-a04a4d759dca)

* PID: 프로세스 ID
 
* TTY: 연결되어 있는 터미널
 
* TIME: 프로세스가 소비한 총 시간 (기본 필드)

* CMD: 사용자가 실행한 명령 이름 (-f, -l, l 옵션)

2. ps aux 사용: 모든 프로세스 확인

![image](https://github.com/namoikmn/helloworld/assets/133830049/58217939-4b5f-41ba-acde-0bb9ed89580d)

3. ps aux 0-r 사용: RSS 값 기준 내림차순 정렬

![image](https://github.com/namoikmn/helloworld/assets/133830049/48f55fc4-b16e-4689-90d7-93219ee81e66)

## 3. jobs
### 개념
현재 세션의 작업 상태를 출력

![image](https://github.com/namoikmn/helloworld/assets/133830049/76af37b2-96a9-42b3-89c5-07162c6554de)

### jobs 옵션
* -l : 프로세스 그룹 ID를 state 필드 앞에 출력한다.

![image](https://github.com/namoikmn/helloworld/assets/133830049/dc8fb5c6-f6a5-479b-bf5a-714202a1ff47)

* -n : 프로세스 그룹 중에 대표 프로세스 ID를 출력한다.
 
* -p : 각 프로세스 ID에 대해 한 행씩 출력한다.

* command : 지정한 명령어를 실행한다.

### 확인할 수 있는 세션 상태
상태 | 설명
------------|----------------------------------
Running | 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임을 뜻한다.
Done | 작업이 완료되어 0을 반환하고 종료했음을 뜻한다.
Done (code) | 작업이 정상적으로 완료했으며, 0이 아닌 코드를 반환했음을 뜻한다.
Stopped | 작업이 일시 중단됨을 뜻한다.
Stopped (SIGTSTP) | SIGTSTP 신호가 작업을 일시 중단했음을 뜻한다.
Stopped (SIGSTOP) | SIGSTOP 신호가 일시 중단했음을 뜻한다.
Stopped (SIGTTIN) | SIGTTIN 신호가 작업을 일시 중단했음을 뜻한다.
Stopped (SIGTTOU) | SIGTTOU 신호가 작업을 일시 중단했음을 뜻한다.

## 4. kill
### 개념
프로세스 종료 명령어

### 옵션
- pid ... : 종료시킬 프로세스 ID나 이름 지정 -> ps 명령어 통해 PID 확인 가능

![image](https://github.com/namoikmn/helloworld/assets/133830049/c097bde5-ee0c-4c16-b2cd-a35f77d5c02e)

pid 프로세스 | 필드명 | 설명
------------|----------|------
Root | USER | 프로세스의 사용자
2518 | PID | 프로세스 ID
0.0 | %CPU | 마지막 1분 동안 프로세스가 사용한 CPU 점유율
0.1 | %MEM | 마지막 1분 동안 프로세스가 사용한 메모리의 점유율
7084 | VSZ | 가상메모리에 있는 프로세스의 KB 단위 크기
1076 | RSS | 프로세스의 실제 메모리의 크기로 KB 단위
? | TTY | 연결되어 있는 터미널
Ss | STAT | 실행되고 있는 프로세스 상태
Jun07 | START | 프로세스가 시작된 날짜
0:00 | TIME | 프로세스가 소비한 총 시간
/usr/sbin/sshd | COMMAND | 사용자가 실행한 명령 이름

- -s: 전달할 시그널의 종류 지정, 이름이나 번호 작성
- -l: 시그널로 사용할 수 있는 시그널의 이름들을 보여줌.
- -1,: -HUP 프로세스 재활성화
- -9: 프로세스 강제종료

### 쉘스크립트 kill, ps 사용 예시
특정 프로세스 종료시키는 쉘 스크립트
```bash
# ps -ef을 이용해서 원하는 프로세스 정보를 얻는다.
var1=$(ps -ef | grep 'run_loop\.sh$')
var2=$(ps -ef | grep 'JenkinsHelper\.jar')

#echo process info : ${var1}
#echo process info : ${var2}

# pid를 얻는다. (공백으로 잘라서, 두번째 argument)
second1=$(echo ${var1} | cut -d " " -f2)
second2=$(echo ${var2} | cut -d " " -f2)

#echo pid : ${second1} / length : ${#second1}
#echo pid : ${second2} / length : ${#second1}

# pid가 존재할 경우 프로세스를 kill 한다.

# -n 스트링은, 문자열 길이가 0 이 아닐 경우 true를 리턴한다.
if [ -n "${second1}" ]
then
        result1=$(kill -9 ${second1})
        echo "process is killed."
else
        echo "running process not found."
fi

if [ -n "${second2}" ]
then
        result2=$(kill -9 ${second2})
        echo "process is killed."
else
        echo "running process not found."
fi
```
