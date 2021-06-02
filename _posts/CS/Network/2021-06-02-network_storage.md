---
title:  DAS, NAS, SAN 차이 정리
excerpt: DAS, NAS, SAN 차이 정리
search: true
categories: 
  - network
tags: 
  - network
last_modified_at: 2021-06-02T15:00:00+09:00
---

## Network Storage(네트워크 스토리지)

1. DAS (Direct Attached Storage)

    - 데이터 서버와 외장형 저장장치를 전용 케이블로 직접(Direct) 접속하는 방법

    - SCSI, IDE, Fiber cable 등의 전용 케이블을 이용

    - 전통적인 접속 방법으로 현재까지도 가장 많이 사용

    - 전용라인의 사용으로 주어진 성능이 보장되며 안정성도 뛰어남
    
    BUT!
    
    - 다른 서버에 할당된 저장 장치영역에는 접근이 금지되어 파일 공유 불가

    - 확장성 및 유연성도 상대적으로 떨어지는 단점


    #### 적은 용량, 데이터 공유가 필요 없는 경우에 사용 가능한 저렴한 솔루션!
  
2. NAS (Network Attached Storage)

    - LAN을 통해서 Storage와 Server를 접속하는 방식

    - LAN을 통해 파일서버와 접속을 하고 파일서버와 Storage 사이에는 SCSI 프로토콜을 기반으로 한 SCSI 또는 Fiber Channel 접속

    - 파일 서버를 통해 파일 시스템의 공유가 가능하며 저장장치와 서버간의 독립성을 유지

    BUT!
    
    - 파일서버에 의해 Storage 용량이 제한 됨

    - 데이터 접근 요청에 의한 파일 서버의 병목현상 발생 가능성 있음

    - 대규모 시스템 환경에서 단일 스토리지 솔루션을 적용하기에는 한계가 있음

    #### SAN이나 DAS보다 저렴한 가격에 대용량의 스토리지를 제공할 수 있어 중규모 프로젝트에 용이
    
3. SAN (Storage Area Network)

    - 서버가 fiber channel switch를 통하여 storage를 연결하는 기법

    - DAS의 접속한계성을 극복하여, n개의 서버가 m개의 스토리지에 접속 가능

    - 전용 네트워크를 통한 고속 입출력 가능

    - 서버간 물리적인 disk 분할 사용
    
    BUT!
    
    - SAN을 구축하기 위해선 많은 비용과 장비들의 투자가 필요함

    - 이기종간의 여러 서버에서 하나의 스토리지를 공유하기 위해선 SAN 매니지먼트 소프트웨어가 별도로 필요하고 SAN 네트워크를 별도로 구축
    
    #### NAS와 DAS를 합쳐놓은 방식, 서버와 스토리지 사이에 Fiber channel switch를 넣어 네트워크 개념을 도입한 방식
