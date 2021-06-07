---
title:  AIX COMMAND 정리
excerpt: AIX COMMAND 정리
search: true
categories: 
  - os
tags: 
  - os
last_modified_at: 2021-06-07T09:00:00+09:00
---

## AIX (Advanced Interface eXcutive) COMMAND 정리

- Volume Group 생성
  
  #smit mkvg
  
  or
  
  #mkvg -y datavg hdisk1 hdisk2
  
  -> hdisk1, hdisk2라는 물리 디스크를 합쳐 datavg라는 vg를 생성
  
  option
  
  -y : volume group의 이름 설정
  
  -S : Scalable VG로 생성
  
- Volume Group list 확인

  #lsvg
  
  option
  
  -o : activate 중인 VG만 출력
  
- 특정 VG의 PV 확인

  #lsvg -p rootvg
  
  #lsvg -l rootvg
  
  option
  
  -p : 지정한 VG 내의 PV의들에 대한 정보 출력
  
  -l : 지정한 VG 내의 LV의들에 대한 정보 출력
  
- VG 정보 변경

   #smit chvg
   
   or
   
   #chvg -a n -Q n datavg
   
   option
   
   -a : 시스템이 시작될 때 VG가 켜지게 할 지
   
   -Q : Quorum에 대해 결정, default는 y
  
  
