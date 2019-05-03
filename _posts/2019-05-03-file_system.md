---
title: 리눅스의 파일 시스템
date: 2019-05-03 23:06
tags: [Linux, File System, Hard Link]
---
리눅스에서 파일 File 이란 개념은 다음과 같이 세 가지로 분류한다.  
1. 넓은 의미의 파일
2. 좁은 의미의 파일
3. 스트림  
<!--more-->
### 넓은 의미의 파일  
bash에서 ls 명령어 입력 시 나오는 모든 것.  
### 좁은 의미의 파일  
* 보통 파일 regular/normal file
* 디렉토리 directory
* 심볼릭 링크 symbolic(soft) link
* 디바이스 device
  
---
  
터미널에서 ls -l 명령어를 입력해보자.  
이때 파일명을 비롯해 표시된 정보들을 메타 데이터라고 하는데  
각 요소들의 의미는 아래와 같다.  
![ls_l](https://user-images.githubusercontent.com/17706039/57145173-95ddb800-6dfd-11e9-9cfe-9c8cee87d942.png){:.rounded}
  
하드링크란 무엇일까?
{:.warning}  
하드링크는 원본 파일과 이름만 다른 동일 파일이라고 보면 된다.  
원본 파일과 하드링크된 파일은 inode를 공유하기 때문에  
하드링크 파일이 수정되면 원본 파일 또한 수정된다.  
![hard_link](https://user-images.githubusercontent.com/17706039/57146525-7b590e00-6e00-11e9-9eda-be17edff6114.png){:.rounded}
  
ln 명령어를 사용하여  
sum.c라는 원본 파일에 대해 hl_sum.c라는 하드링크 파일을 생성했다.  
그 후, ls에 -i 옵션을 주어 파일들의 inode 번호를 확인했다.  
두 파일의 inode 번호가 일치한다는 것을 확인할 수 있었다.  
  
---
  
터미널에서 mount -t ext4 를 입력해보자.  
파티션의 개수만큼 문자열이 출력될 것이다.  
![mount](https://user-images.githubusercontent.com/17706039/57146881-59ac5680-6e01-11e9-9adf-c59cf4576a3e.png){:.rounded}
출력 문자열이 의미하는 바는  
시스템의 첫 번째 디스크의 첫 번째 파티션이 ext4 파일 시스템을 사용하며  
루트(/) 디렉토리에 마운트되어 있음을 의미한다.