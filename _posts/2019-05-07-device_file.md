---
title: 디바이스 파일
date: 2019-05-07 21:09
tags: [Linux, File System, Device File]
---
리눅스의 파일 시스템은 디바이스를 파일로 표현한다.  
디바이스 파일에 대해 알아보자.  
<!--more-->
### 디바이스 파일  
/dev 디렉토리를 확인해보자.  
이 디렉토리에 시스템과 연결된 모든 디바이스들이 파일로써 보관되어 있다.  
![dev](https://user-images.githubusercontent.com/17706039/57298930-5de0b880-710e-11e9-82c8-e0f8d392f25a.png){:.rounded}
  
디바이스 파일은 문자 디바이스 파일과 블록 디바이스 파일로 나뉜다.  
### 문자 디바이스 파일  Character device file  
문자 디바이스란 입력 혹은 출력하는 데이터가 순차적인 성질을 가지는 디바이스이다.  
문자 디바이스는 데이터를 문자(character) / byte 단위로 읽고 쓴다.  
문자 디바이스로 키보드, 프린터, 마우스, 콘솔 등이 있다.  
  
### 블록 디바이스 파일 Block device file  
블록 디바이스는 데이터를 블록 단위로 읽고 쓴다.  
블록 디바이스의 예로 HDD, SSD, CD/DVD 등이 있다.  
  
---
  
/dev/block 디렉토리에 블록 디바이스 파일들의 심볼릭 링크가 모여있다.  
![block](https://user-images.githubusercontent.com/17706039/57299838-8c5f9300-7110-11e9-8b2f-99f63307f899.png){:.rounded}
  
심볼릭 링크 파일명의 의미는 다음과 같다.  
X : Y -> X는 디바이스의 id, Y는 디바이스의 객체 id
{:.info}  
디바이스 드라이버 종류의 id는 /proc/devices 파일을 통해 확인할 수 있다.  
![devices](https://user-images.githubusercontent.com/17706039/57311844-60034100-7127-11e9-96ba-a2f6daa96f98.png)
  
/dev/block/ 아래의 파일 중 sda와 sda1은  
각각 시스템의 첫 번째 디스크, 첫 번째 디스크의 첫 번째 파티션을 의미한다.  
위의 이미지에서 sd(= SCSI Disk)의 id가 8임을 알 수 있다.  
이제 sda와 sda1을 가리키는 심볼릭 링크 파일명이 왜 8:0, 8:1인지 알 거 같다.