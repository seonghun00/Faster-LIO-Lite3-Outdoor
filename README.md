<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=80&section=header" width="100%" />
</p>


🤖 Faster-LIO for Lite3 Outdoor Mapping
Lite3 4족 보행 로봇을 위한 야외 SLAM 최적화 프로젝트
영남대학교 본부 광장 야외 맵핑 효율성을 높이기 위해 Faster-LIO의 Voxel Grid 및 Z-axis 데이터 필터링을 구현했습니다.

🌟 Project Overview
본 프로젝트는 Unitree Lite3 로봇과 Livox Mid-360 LiDAR를 활용하여 야외 환경에서의 맵핑 성능을 개선하는 데 목적이 있습니다. 야외 환경의 방대한 3D 포인트 클라우드 데이터를 실시간으로 처리하기 위해 연산 효율성을 극대화하는 최적화 로직을 추가했습니다.

🛠 Key Optimizations (Technical Depth)
1. Voxel Grid Filter Optimization
Problem: 야외 광장은 데이터가 매우 방대하여 실시간 Odometry 연산 시 CPU 부하가 급증함.

Solution: 전체 Voxel Grid Size를 환경에 맞춰 최적화하여 포인트 클라우드 밀도를 전략적으로 조절했습니다. 이를 통해 시스템의 실시간성을 보장하면서도 맵의 정밀도를 유지했습니다.

2. Z-axis Bound Filtering
Problem: 야외 맵핑 시 하늘(무한대 데이터)이나 지면의 불필요한 노이즈 데이터가 포함되어 데이터 처리량이 불필요하게 늘어남.

Solution: 데이터 처리 범위의 **Z값 상한선(Upper Bound) 및 하한선(Lower Bound)**을 명확히 정의했습니다.

특정 높이 이상의 불필요한 데이터(나무 위, 하늘 등)를 사전에 제거하여 데이터 처리량을 획기적으로 감축.

연산 부담(Computational Load)을 줄임으로써 배터리 효율 및 로봇 제어 안정성 향상.

📊 Mapping Result
영남대학교 대학 본부 광장 (YU Plaza)
로봇이 직접 광장을 주행하며 생성한 2D/3D 지도 데이터입니다. 중앙의 'YU' 로고와 주변 지형이 최적화된 필터링을 통해 깔끔하게 구현되었습니다.

<p align="center">
<img src="./assets/대학 본부 맵핑 사진.png" width="500" alt="Mapping Result at Yeungnam University" />
</p>

⚙️ Environment
Robot: Unitree Lite3 (4-legged Robot)

LiDAR: Livox Mid-360

Algorithm: Faster-LIO (Modified)

OS: Ubuntu 20.04 (ROS1 Noetic)

© 2026 Seong-hun Bae.
