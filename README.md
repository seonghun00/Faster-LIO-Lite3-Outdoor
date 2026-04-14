<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=120&section=header" width="100%" />
</p>

# 🤖 Quadruped Robot Outdoor Mapping Optimization
> **Faster-LIO 기반 Lite3 로봇의 야외 환경 매핑 데이터 최적화**

---

## 🚀 Key Features
* **Real-time SLAM**: Faster-LIO 알고리즘을 활용한 고속 4족 보행 로봇 맵핑
* **Voxel Grid Optimization**: 환경에 최적화된 Voxel 크기 조절을 통해 연산량 절감
* **Z-axis Range Filtering**: 상·하한값(Z-limit) 설정을 통한 노이즈 데이터 차단
* **Data Efficiency**: 방대한 3D 데이터를 시스템 부하 없이 처리하는 경량화 파이프라인

---

## 🛠 Tech Stack
* **Robot**: Unitree Lite3 (Quadruped Robot)
* **Sensor**: Livox Mid-360 LiDAR
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

### 📍 영남대학교 대학 본부 광장 (YU Plaza)
최적화된 필터링 로직을 통해 노이즈 없이 깔끔하게 구현된 야외 광장 맵입니다.

<p align="center">
  <img width="342" height="388" alt="대학 본부 맵핑 사진" src="https://github.com/user-attachments/assets/8ea24905-06d3-40e3-894e-8229d5ae2fa4" />
</p>

---

## 💻 How to Run
1. **Dependency**: `Livox-SDK2` 및 `Faster-LIO` 환경 구성 확인
2. **Parameters**: `config/params.yaml`에서 Voxel 크기와 Z-limit 값 조정
3. **Launch**: 로봇과 LiDAR 연결 후 전용 Launch 파일 실행

---

© 2026 Seong-hun Bae.
