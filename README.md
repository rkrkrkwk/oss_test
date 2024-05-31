# 오픈소스SW 과제

20194578 김동권

리눅스 명령어 중에서 **[top](https://github.com/rkrkrkwk/oss_test/blob/main/README.md#top), [ps](https://github.com/rkrkrkwk/oss_test/blob/main/README.md#ps), [jobs](https://github.com/rkrkrkwk/oss_test/blob/main/README.md#jobs), [kill](https://github.com/rkrkrkwk/oss_test/blob/main/README.md#kill)** 명령어에 대해서 조사해보자!

## top

시스템의 상태를 전반적으로 알 수 있게 해준다.

옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.

### top 명령어 수행 시 나타나는 내용
```
top - 09:37:25 up 12 min,  0 users,  load average: 0.02, 0.08, 0.09
Tasks:   2 total,   1 running,   1 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 98.8 id,  0.9 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15964.5 total,  14094.4 free,    749.0 used,   1121.1 buff/cache
MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.  14943.3 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    1 root      20   0    4248   3324   2784 S   0.0   0.0   0:00.00 bash
   13 root      20   0    6096   3192   2684 R   0.0   0.0   0:00.06 top
```

- `top - 09:37:25 up 12 min,  0 users,`

현재 시간과 서버가 구동되고있는 시간, 유저 수를 보여준다.

- `load average: 0.02, 0.08, 0.09`

각각 1분, 5분, 15분 평균 프로세스 수를 보여준다.

- `Tasks:   2 total,   1 running,   1 sleeping,   0 stopped,   0 zombie`

프로세스의 수를 보여준다.

총 2개의 프로세스가 있고 1개는 실행중, 1개는 sleeping 상태이다.

- `%Cpu(s):  0.1 us,  0.2 sy,  0.0 ni, 98.8 id,  0.9 wa,  0.0 hi,  0.0 si,  0.0 st`

cpu 사용률을 보여준다.

us : 사용자 CPU 사용률

sy : 시스템 CPU 사용률

ni : 우선순위가 낮은 프로세스 CPU 사용률

id : 유휴 상태 CPU 사용률

wa : I/O 대기중 cpu 사용률

hi : 하드웨어 인터럽트 cpu 사용률

si : 소프트웨어 인터럽트 cpu 사용률

st : 가상 CPU가 실제 CPU를 기다리는 시간

- `MiB Mem :  15964.5 total,  14094.4 free,    749.0 used,   1121.1 buff/cache`

메모리 사용률을 보여준다.

- `MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.  14943.3 avail Mem`

스왑 메모리 사용율을 보여준다.

- 프로세스

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    1 root      20   0    4248   3324   2784 S   0.0   0.0   0:00.00 bash
   13 root      20   0    6096   3192   2684 R   0.0   0.0   0:00.10 top
```

현재 프로세스를 보여준다.

PID : 프로세스 ID

USER : 프로세스 사용자

PR : 우선 순위

NI : 우선 순위

VIRT : 가상 메모리 양

RES : 물리 메모리 양

SHR : 공유 메모리 크기

S : 프로세스 상태

%CPU : CPU 사용량

%MEM : 메모리 사용량

TIME+ : 사용한 CPU 시간

COMMAND : 명령어 이름

### top -b

순간 순간의 내용을 볼 수 있다.

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/29464940-4559-4a0b-ab05-f333905bb8f4)

### top -n (숫자)

해당 숫자만큼 실행하고 종료한다.

만약 3일경우 3초마다 갱신되므로 9초동안 실행되고 종료된다.

### top 실행 후 명령어

- Z

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/f3c0d218-bd3e-4b32-99ff-21f292e2bd02)

각각 요소의 색을 커스텀 가능하다.

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/4b108238-8eba-4406-9ce8-cf9877149952)

- E , e

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/64474fba-17d7-4d81-9b95-2ee5b1a4e8f6)

단위를 바꿀 수 있다.

- t, m

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/1546fd46-e6a1-4e7b-b236-a73590a8df1c)

메모리, cpu 사용률을 시각화 할 수 있다.

- 1 , 0

![image](https://github.com/rkrkrkwk/oss_test/assets/166924793/29ca8e57-98ed-490e-b971-2dfbc888f26f)

1은 cpu를 각 코어별로 확인할 수 있다.

0은 0 값을 없애준다.

- < , >

프로세스의 정렬 순서를 바꾼다.

- J

프로세스의 각 요소를 왼쪽 정렬, 오른쪽 정렬 할 수 있다.

- k

프로세스를 종료한다.

- d, s

갱신 시간을 바꾼다.

- q

top 명령어를 종료한다.

- h

명령어를 보여준다.



## ps

## jobs

## kill
