---
title:  Face Detection Example
excerpt: 기본적인 face detection을 예제 코드를 통해 복습
search: true
categories: 
  - AI
tags: 
  - AI
last_modified_at: 2020-12-23T19:00:00+09:00
---

## Face Detection(얼굴 인식)

기본적인 face detection을 예제 코드를 통해 복습!

```python
from google.colab import drive
drive.mount('/gdrive')

!pip install face_recognition

import cv2
import face_recognition as fr
from matplotlib import pyplot as plt
```

pre-built되는 library가 있지만, 항상 최신 버전으로 지원하고 있지 않기 때문에,

때론 `!pip install 패키지` 명령어를 통해 업그레이드 해줘야할 필요가 있다.



### 사진속의 사람들의 얼굴을 인식하고 체크해보자!

```python
image_path = '/gdrive/My Drive/Colab/redvelvet.jpg'

image = fr.load_image_file(image_path)
face_location = fr.face_locations(image)

for(top, right, bottom, left) in face_location:
  cv2.rectangle(image, (left, top), (right, bottom), (0, 0, 255), 3)

# 이미지 버퍼 출력
plt.rcParams["figure.figsize"] = (16, 16)
plt.imshow(image)
plt.show()
```

fr.face_locations : 사진에 등장하는 모든 얼굴을 search

![](https://user-images.githubusercontent.com/40141212/102996144-e3281380-4565-11eb-9e25-c3c000a1f151.png)

코드 결과 image!

![image-20201223200937216](https://user-images.githubusercontent.com/40141212/102996340-4f0a7c00-4566-11eb-9ed6-ba556b8ddb90.png)



### 사진속의 사람의 얼굴을 잘라내서 비교해보자!

```python
plt.rcParams["figure.figsize"] = (1, 1)

# 이미지 파일을 로드하여 known_person_list 리스트 생성
known_person_list = []
known_person_list.append(fr.load_image_file('/gdrive/My Drive/Colab/jin.jpg'))
known_person_list.append(fr.load_image_file('/gdrive/My Drive/Colab/rm.jpg'))
known_person_list.append(fr.load_image_file('/gdrive/My Drive/Colab/jayhob.jpg'))
known_person_list.append(fr.load_image_file('/gdrive/My Drive/Colab/vui.jpg'))
known_person_list.append(fr.load_image_file('/gdrive/My Drive/Colab/jungguk.jpg'))

# 얼굴만 쏙 뽑아내는 코드
known_face_list = []
for person in known_person_list:
  top, right, bottom, left = fr.face_locations(person)[0]
  face_image = person[top:bottom, left:right]

  known_face_list.append(face_image)

for face in known_face_list:
  plt.imshow(face)
  plt.show()
```

![image-20201223204935450](https://user-images.githubusercontent.com/40141212/102996389-68132d00-4566-11eb-8377-6e8019532f4b.png)


```python
unknown_person = fr.load_image_file('/gdrive/My Drive/Colab/me.jpg')

top, right, bottom, left = fr.face_locations(unknown_person)[0]
unknown_face = unknown_person[top:bottom, left:right]

plt.title("unknown_face")
plt.imshow(unknown_face)
plt.show()
```

![image-20201223205010308](https://user-images.githubusercontent.com/40141212/102996430-795c3980-4566-11eb-929e-cecee67cdf25.png)


```python
enc_unknown_face = fr.face_encodings(unknown_face)

plt.imshow(enc_unknown_face)
plt.show()

for face in known_face_list:
  enc_known_face = fr.face_encodings(face)

  distance = fr.face_distance(enc_known_face, enc_unknown_face[0])

  plt.title("distance: " + str(distance))
  plt.imshow(face)
  plt.show()
```

fr.face_encoding : 68개의 좌표를 128개의 숫자로 변환한다. 128개의 숫자는 deep learning의 결과물이기에 각 숫자의 의미는 알수 없다.

![image-20201223211009664](https://user-images.githubusercontent.com/40141212/102996477-8aa54600-4566-11eb-90ff-6c7b276a517e.png)


### 느낀점

colab을 통해 face detection을 너무나 쉽게 해볼 수 있는 점이 좋았다.

내가 가장 닮은 사람은 Jin이다.
