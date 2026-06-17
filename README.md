<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=80&section=header" width="100%" />
</p>

# 🤖 Quadruped Robot Outdoor Mapping Optimization
> **Faster-LIO 기반 Lite3 로봇의 야외 환경 매핑 데이터 최적화**
<p align="left">
  <a href="https://releases.ubuntu.com/20.04/"><img src="https://img.shields.io/badge/Ubuntu_20.04-E95420?style=flat&logo=ubuntu&logoColor=white"></a>
  <a href="http://wiki.ros.org/noetic"><img src="https://img.shields.io/badge/ROS_Noetic-22314E?style=flat&logo=ros&logoColor=white"></a>
</p>

4족 보행 로봇은 보행 시 발생하는 진동이 LiDAR 데이터의 품질을 저하시키고 실시간 연산에 부담을 줌. Faster-LIO 알고리즘을 Lite3 로봇에 최적화하여, 야외 광장과 같은 넓은 환경에서 끊김 없고 정확한 3D 맵을 실시간으로 생성하는 시스템 구축을 목적.

---

## 📂 Core Modules (수정한 파일 바로가기)
> 야외 경사로 및 노이즈 환경 최적화를 위해 수정하고 반영한 핵심 모듈입니다.

* 📄 [laser_mapping.cc](faster-lio/src/laser_mapping.cc) :로봇이 기울어져도 실제 바닥 고도를 정확하게 인식하여 노이즈를 걸러내는 핵심 필터 코드 구현
* 📄 [c16.yaml](faster-lio/config/c16.yaml) : 야외 환경 최적화용 전역 Z축 상·하한 한계값(Z-limit) 파라미터 정의
* 📄 [mapping_c16.launch](faster-lio/launch/mapping_c16.launch) : 설정한 Z축 높이 필터 기준값들로 실시간 매핑 실행하는 런치 파일

---

## 🚀 Key Features
* **Real-time SLAM**: Faster-LIO 알고리즘을 활용한 고속 4족 보행 로봇 맵핑
* **Voxel Grid Optimization**: 환경에 최적화된 Voxel 크기 조절을 통해 연산량 절감
* **Z-axis Range Filtering**: 상·하한값(Z-limit) 설정을 통한 노이즈 데이터 차단
* **Data Efficiency**: 방대한 3D 데이터를 시스템 부하 없이 처리하는 경량화 파이프라인

---

## 🛠 Tech Stack
* **Robot**: Deep Robotics Lite3 (Quadruped Robot)
* **Sensor**: lslidar-C16 (360)
* **OS**: Ubuntu 20.04 (ROS Noetic)
* **Algorithm**: Faster-LIO (Optimized)

---

## 🏗 Optimization Logic (핵심 역량)

### 1. Voxel Grid Downsampling
야외 광장의 방대한 포인트 클라우드를 실시간으로 처리하기 위해 Voxel 크기를 최적화했습니다. 이를 통해 메모리 점유율을 낮추고 오도메트리 연산 속도를 대폭 개선했습니다.

### 2. Z-axis Thresholding (Data Reduction)
매핑에 불필요한 데이터를 사전에 필터링하여 시스템 부담을 최소화했습니다.
* **Upper Bound**: 하늘, 나무 상단 등 불필요한 고고도 노이즈 제거
* **Lower Bound**: 바닥 지면 아래의 오차 및 불필요한 반사 데이터 차단

---

## 📸 Mapping Results

### 📍 학과 건물 실내·외 매핑 결과 (.pcd)
최적화된 필터링 로직을 적용하여 노이즈를 효과적으로 억제하고 정밀하게 생성된 실내외 복합 환경의 Point Cloud Data 결과물입니다.

<p align="center">
  <img src="https://github.com/user-attachments/assets/cb7b84ce-d115-4013-a569-622ee8d0297d" width="48%" alt="실내 환경 PCD" />
  <img src="https://github.com/user-attachments/assets/11251370-f608-4a21-a134-3449291945b2" width="48%" alt="실외 환경 PCD" />
</p>


### 📍 대학 본부 광장 전체 매핑 결과
<p align="center">
  <img width="500" alt="대학 본부 맵핑 사진" src="https://github.com/user-attachments/assets/8ea24905-06d3-40e3-894e-8229d5ae2fa4" />
</p>

---

## 💻 How to Run
1. **Dependency**: `Livox-SDK2` 및 `Faster-LIO` 환경 구성 확인
2. **Parameters**: `config/params.yaml`에서 Voxel 크기와 Z-limit 값 조정
3. **Launch**: 로봇과 LiDAR 연결 후 전용 Launch 파일 실행

---

> **Notice:** 본 레포지토리는 프로젝트가 모두 종료된 이후, 개인 기록 및 아카이브 목적으로 사후 구축되었습니다.
* 실제 로봇 실험 당시의 하드웨어 세팅, 센서 캘리브레이션, 의존성 패키지 환경이 완벽히 복원되지 않았을 수 있으므로 환경에 따라 정상적으로 동작하지 않거나 추가적인 파라미터 튜닝이 필요할 수 있습니다.
* 코드 활용 시 참고용으로만 사용하시기를 권장하며, 실제 구동 시 발생할 수 있는 오류에 유의하시기 바랍니다.

---

© 2026 Seong-hun Bae.
