# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 정재훈
- 리뷰어 : 서인하


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 중요! 해당 조건을 만족하는 부분을 캡쳐해 근거로 첨부
<img width="758" height="976" alt="image" src="https://github.com/user-attachments/assets/53a43171-87ce-4b09-a623-ca21f3474020" />
4가지 왜곡 조건(전체 왜곡 / 배경만 왜곡 / 초소형 객체 / 부분 가림)에서 CAM vs Grad-CAM 성능을 IoU로 정량 비교하는 최종 실험까지 완성되어 있습니다.
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
<img width="821" height="812" alt="image" src="https://github.com/user-attachments/assets/0eea2c9a-c45b-4afc-bf65-259a24100d9c" />
가장 핵심 코드인 generate_grad_cam에서 forward hook / backward hook의 역할, gradient GAP으로 weight를 계산하는 과정, ReLU 적용 이유까지 각 단계별로 인라인 주석이 명확하게 달려 있어 코드 흐름을 쉽게 따라갈 수 있었습니다.

- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
<img width="1018" height="763" alt="image" src="https://github.com/user-attachments/assets/bdf4de80-355f-4d23-930d-ee3a6b631618" />
기본 요구사항 외에 4가지 독창적인 실험 조건(전체 이미지 왜곡, 배경만 왜곡, 초소형 객체, 부분 가림)을 직접 설계하고, layer3 vs layer4를 교차 비교하는 체계적인 ablation study를 수행했습니다.
        
- [x]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
<img width="1016" height="738" alt="image" src="https://github.com/user-attachments/assets/3f4cdbcb-5ca3-4b9d-93c8-af46f64b3bb6" />
4가지 실험 조건별로 결과를 수치 기반으로 분석하고, "왜 그런 결과가 나왔는가"에 대한 원인(GAP 구조의 수학적 동치, layer별 해상도 차이 7×7 vs 14×14, IoU 지표 특성 등)을 명확히 서술하여 단순 결과 나열이 아닌 깊이 있는 회고를 작성하였습니다.

- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
<img width="995" height="1054" alt="image" src="https://github.com/user-attachments/assets/234419c2-b8d1-49a5-892f-666fdde5ba21" />
run_localization_test, visualize_both_bbox_on_image, get_bbox, get_iou 등 반복 사용되는 로직을 함수로 모듈화하여 실험 조건이 바뀌어도 함수 인자(target_layer_name, threshold 등)만 교체하면 재사용 가능한 구조로 잘 설계되었습니다.


# 회고(참고 링크 및 코드 개선)
```
# CAM과 Grad-CAM이 GAP+Linear 구조에서 수학적으로 동치임을 코드 실험으로 직접 확인할 수 있어서
# 이론으로만 알던 내용을 체감하는 좋은 기회였습니다.
```
