### Introduction
컴퓨터 그래픽스와 시각효과 기술의 발전은 인간과 유사한 고품질의 디지털 휴먼을 제작 가능하게 하며, 이러한 디지털휴먼은 가상과 현실 공간의 경계를 허무는 역할을 한다. 디지털휴먼은 관객과 상호작용을 통해 콘텐츠에 대한 높은 몰입감을 이끌어낼 수 있으며, 블록버스터 영화, 트리플 A 게임, 엔터테인먼트 산업 등에서 광범위하게 활용되고 있다. 따라서 디지털 휴먼 제작에 있어 '얼마나 사실적인 디지털휴먼을 제작할 수 있는가'는 필수적인 요소로, 이는 컴퓨터 그래픽스의 주된 목표 중 하나이다. 초기 페이셜 캡처 파이프라인은 'LightStage' 시스템으로 다수의 카메라를 통해 얼굴 이미지 데이터를 획득하고, 얼굴 반사율을 캡처하여 사실적인 얼굴 외형을 제작하는 방식으로 이루어졌다[1]. 또한 편광 그래디언트 기반 조명을 사용하였고, 더 나아가 얼굴 캡처 시스템과 페이셜 마커를 기반으로 사실적인 디지털휴먼 외형을 제작했다[2],[3]. 이러한 포토그래메트리를 활용한 페이셜 캡처는 디지털휴먼 얼굴 생성 시간을 줄이고 '불쾌한 골짜기' 문제를 해결하는 데 기여하였다[4]. 하지만, 포토그래메트리를 활용한 페이셜 캡처 방법론은 얼굴 스캔 데이터 캡처 시간, 시스템 구축 비용 그리고 전문인력의 필요성이라는 한계를 가지고 있다. 따라서 최근 페이셜 캡처를 통한 디지타이징 연구는 사실적인 디지털휴먼 얼굴 외형을 생성하는 것과 더불어 페이셜 캡처 시간을 단축시키는 것과 시스템 구축 비용에 중점을 둔 연구가 진행되고 있다. 이에 따라 Fyffe는 단안경을 통해 촬영된 비디오 시퀀스에서 고해상도의 얼굴 스캔 데이터를 획득하는 방법을 제시했다. 하지만, 제시된 방법론은 고해상도 스캔 데이터를 얻기 위해 다양한 각도의 얼굴 포즈가 필요하다는 한계를 가지고 있다[5]. 이외 다른 선행 연구자들은 단안경 기반의 캡처 시스템을 구축해 조명이 통제되지 않는 실외 환경에서도 페이셜 캡처 데이터를 획득하는 방법을 제안했다[6],[7],[8]. 제안된 단안경 기반의 캡처 시스템을 통한 페이셜 캡처 방법론은 시스템 구축 비용 절감에 효과적이였지만, 기존 디지타이징 파이프라인에 비해 얼굴 외형의 세부적 표현력이 떨어진다는 한계가 존재했다. 따라서 페이셜 캡처 시스템 구축 비용 절감과 사실적인 디지털휴먼 얼굴 외형을 제작하기 위해 Azinovic은 스마트 폰과 편광 호일을 활용해 페이셜 캡처 디지타이징 시스템을 경량화하는 방법론을 제안했다[9]. 또한 최근에는 'Disney Studio'에서 12대의 DSLR 카메라와 교차 편광과 평행 편광을 활용해 미세한 피부 표면의 스캔 데이터를 획득하고 사실적인 페이셜 캡처 디지타이징 시스템을 제안했다[10]. 더 나아가 패시브 페이셜 캡처 디지타이징 시스템에서의 피부 표면 텍스처 추정 한계를  3D 공간에서 광원 보정을 통해 텍스처와 표면 반사 모델을 결합할 수 있는 방법론을 제안했다[11]. 
현재까지 제안된 페이셜 캡처 디지타이징 방법론은 공통적으로 사실적인 디지털휴먼 얼굴 외형 생성과 시스템 구축 비용 절감, 그리고 최소한의 얼굴 스캔 데이터를 활용한 디지타이징에 중점을 두고 있다. 하지만, 기존 제안된 방법론은 물리적 공간에서 페이셜 캡처 디지타이징 시스템을 구성하는 것으로 페이셜 캡처 디지타이징 시스템을 개발하고 개선하는 데 근본적인 제약을 가지고 있다. 사실적인 디지털휴먼 얼굴 외형을 만들기 위해서는 디지타이징 파이프라인의 개선 뿐만 아니라 카메라와 조명을 포함하는 디지타이징 시스템 개발과 실험 과정이 필요하다. 또한 조명 조건, 카메라 설정, 렌즈 초점거리 등 디지타이징 시스템 내에 다양한 변수에 따라 얼굴 스캔 데이터 특성이 변화되어 사실적인 디지털휴먼 얼굴 외형을 생성하기 위해서는 이러한 변수들을 고려할 필요가 있다. 이러한 변수들은 디지털휴먼을 개발하는 VFX 스튜디오마다 구성 요소가 달라 일정한 결과물이 아닌 상이한 결과물을 만들어내며, 이에 따라 전문적인 디지털 아티스트 참여가 필수적이다. 더 나아가 생성된 얼굴 외형의 질적평가는 디지털 아티스트의 주관적 판단을 통해 이루어지며, 이러한 정성적 평가는 페이셜 캡처 디지타이징 파이프라인 최적화에 한계가 있을 수 있다. 이처럼 물리적 공간에서의 페이셜 캡처 디지타이징 시스템 파이프라인을 개선하는 과정은 다양한 변수로 인한 비용과 인적 소모가 크기 때문에 새로운 페이셜 캡처 디지타이징 시스템 파이프라인 방법론의 개발이 요구되고 있다.
따라서 본 연구에서는 물리적 공간에서 이루어지는 페이셜 캡처 디지타이징 시스템 파이프라인 한계를 해결하기 위해 디지털 트윈을 활용한 페이셜 캡처 디지타이징 파이프라인을 제안한다. 디지털 트윈은 주로 파이프라인 최적화를 위해 활용되는 방법론으로, 물리적 공간을 모사한 가상공간에서 데이터의 생산 효율성을 향상시키고 데이터 분석 및 파이프라인 개선을 통해 물리적 공간에서의 예상되는 상황을 예측하는 데 사용된다[12]. 이에 본 연구에서 제안된 디지털 트윈을 활용한 페이셜 캡처 디지타이징 파이프라인은 물리적 공간을 반영한 가상공간의 디지타이징 시스템에서 시뮬레이션을 통해 문제를 탐지하고 개선하여, 다시 물리적 공간에 적용한다. 본 연구에서 제안된 방법론은 여러 가지 측면에서 기존 물리적 공간에서의 파이프라인 한계를 극복할 수 있으며 효율적인 결과를 도출할 수 있는 방안을 제시한다. 첫 번째로, 디지타이징 변수를 바꾸는 데 있어서 노동 집약적이며 수동적인 수정 과정은 가상공간에서의 조작을 통해서 크게 단순화될 수 있다. 이는 사용자가 복잡한 과정없이 카메라의 위치, 조명 조건, 렌즈 초점거리를 조절하여 다양한 시뮬레이션을 가능하게 한다. 두 번째로, 양질의 결과물을 얻기 위해 페이셜 캡처 디지타이징 파이프라인을 최적화에 소요되는 시간과 비용을 줄일 수 있다. 이는 가상공간에서의 자동화된 과정을 통해 빠르고 정확한 피드백을 받아 결과물을 지속적으로 개선하여 최적의 결과를 만들어낸다. 세 번째로, 기존 파이프라인의 경우 전문적인 아티스트의 주관적인 판단에 의해 평가가 이루어졌다면, 제안된 방법은 가상공간에서 기 구축된 디지털 휴먼을 Ground Truth로 활용해 시뮬레이션을 진행하여 생성된 얼굴 지오메트리를 정량적으로 평가하고 개선할 수 있다. 마지막으로 가상공간에서 방대한 시뮬레이션을 통해 생성된 얼굴 스캔 데이터는 딥러닝 기반 학습 데이터로 활용될 수 있다. 이를 통해 효과적인 학습이 이루어질 수 있으며, 더욱 사실적이고 정밀한 얼굴 외형을 생성하는 데 기여할 수 있다. 
이처럼 본 연구는 디지털 트윈을 통한 페이셜 캡처 디지타이징 파이프라인을 최적화하는 데 목표를 두고 있으며, 기존 물리적 공간에서 이루어지던 페이셜 캡처 R&D 파이프라인에 디지털 트윈 방법론을 도입하는데 중점을 둔다. 구체적으로는 물리적 공간 특성을 반영한 가상공간 구축과 이를 통해 페이셜 캡처 디지타이징 시스템에서 결과물에 영향을 미치는 변수를 조절하여 페이셜 스캔 데이터를 획득한다. 이어서 획득된 데이터를 기반으로 얼굴 지오메트리를 재구성하고, 정량적 평가를 통해 페이셜 캡처 디지타이징 파이프라인 최적화를 목표로 한다.

### Related Work

#### Active Facial Capture System

고품질의 얼굴 스캔 데이터 획득을 위해서는 일반적으로 Active Facial Capture System이 활용되는 경향이 있다. Debevec에 의해 진행된 Active Facial Capture System 초기 연구는 특정한 조명 패턴을 사용해 얼굴 피부의 반사율 데이터를 획득하는 방법을 제시했다[1]. 제안된 방법론은 사람의 얼굴을 디지털로 재현하는 데 큰 영향을 미쳤으며, 이후 'LightStage' 페이셜 캡처 시스템에 대한 기초를 마련했다. 다만, 제안된 방법론은 페이셜 스캔 데이터를 획득하는 과정에서 피사체가 움직이지 않아 동적인 페이셜 데이터를 획득하는 데 한계가 있다. 이후 Weyrich는 150개 조명, 16개 카메라로 구성된 LED 구체를 통해 피부 영역마다 확산, 반사, 거칠기 정도를 측정해 고품질의 피부를 재현하는 방법론을 제시한다[13]. 하지만, 이 방법론은 통제된 환경에서 광범위한 데이터를 수집해야 하고, 정확도 향상을 위한 많은 계산량으로 컴퓨팅 리소스 한계가 존재한다. 이처럼 초기 Active Facial Capture System 디지타이징 파이프라인은 구 형태의 캡처 시스템을 활용해 고품질의 얼굴 스캔 데이터를 획득하고 사실적인 디지털 휴먼 얼굴을 생성했지만, 상당한 양의 페이셜 스캔 데이터가 필요했다. 따라서 선행 연구자들은 페이셜 스캔 데이터의 양을 줄이며, 사실적인 디지털 휴먼 얼굴을 생성하는 연구 방향에 중점을 두고 있다. 이에 Ma는 편광 구면의 그라데이션 조명을 활용해 8장의 이미지 데이터에서 정반사와 난반사를 분리하는 모델을 제안해, 페이셜 캡처 디지타이징 시스템의 속도를 높여 동적인 표정을 캡처하는데 기여하였다[14]. 더 나아가 Ghosh는 피부를 계층적인 층으로 인식해 피부 반사율을 획득하는 방법과 편광 그라데이션 조명을 활용한 멀티 뷰 캡처 방식을 제안했다[15],[16]. 이는 피부의 다양한 계층적 반사율을 적용해 기존에 표현하기 어려웠던 수염, 피부 깊이를 표현할 수 있어 사실적인 얼굴 외형 표현을 가능하게 했다. 이러한 방법론은 그라데이션 조명을 통해 데이터 획득에 있어 빠르다라는 장점이 있지만, 여전히 LED 구체를 사용해야한다는 한계가 있다. 이에 Fyffe는 페이셜 캡처 파이프라인 시스템을 소비자 하드웨어를 활용해 구축하여 얼굴 외형과 피부 반사율을 즉각적으로 캡처하는 방법론을 제안했다[16].
이처럼 페이셜 캡처 디지타이징 파이프라인에서의 연구 과제는 사실적인 디지털 휴먼 얼굴을 재현하는 것을 넘어, 동적인 표정과 움직임을 사실적으로 생성하는 것으로 이어진다. 따라서 페이셜 캡처 디지타이징 시스템에서는 정적인 페이셜 캡처뿐만 아니라 주요 얼굴 표정간의 반사율을 획득하고 보간하는 모델을 통해 제안함으로 다양한 얼굴 표정의 애니메이션을 사실적으로 렌더링할 수 있게 되었다[17],[18]. 더 나아가 Wenger는 생성된 디지털 휴먼 얼굴 표정을 리라이팅하기 위해 LED 구와 고속 촬영을 통해 얼굴 스캔 데이터의 반사율을 추정하는 방법론을 제안했고, 이는 얼굴 표정을 동적으로 리라이팅할 수 있어 포스트 프로덕션에서 상당한 유연성을 제공한다[19]. Nagano 역시 얼굴 표정의 동적 표현에 있어 모공과 같은 미세 구조를 강조하는 표현 방법을 제안하고 획득된 데이터는 디스플레이스먼트 맵으로 확장되어 복잡한 피부 디테일을 간결하게 표현할 수 있게 되었다[20]. 하지만, 여전히 여러 대의 카메라를 통해 이미지 데이터를 획득해야한다는 한계점이 존재했다. 따라서 Fyffe는 편광 컬러 그라데이션 조명을 활용하여 하나의 이미지에서 피부 반사율을 측정하는 모델을 제시하였고, 피부 표면 아래의 산란과 반사를 분리할 수 있어 파이프라인의 간소화의 이점을 가질 수 있다[21]. 더 나아가 최근에는 Meka가 구면 그래디언트 조명을 보색으로 활용해 페이셜 스캔 데이터를 획득해 동적으로 스캔 데이터를 리라이팅할 수 있는 방법을 제안했다[22]. 또한 머신러닝을 활용해 얼굴 표정을 동적으로 재조명할 수 있지만, 머신러닝 네트워크를 학습하기 위한 데이터가 필요하며, 표준 렌더링 파이프라인에서 활용할 수 있는 반사 맵이 생성되지 않는 한계가 존재한다.

#### Passive Facial Capture System

Passive Facial Capture System은 Active Facial Capture System 방식의 복잡성과 환경적 제약을 극복하기 위한 대안으로 주목받아왔다. Passive Facial Capture System의 경우 주로 자연광 혹은 주변광을 활용해 피부의 색상과 디테일을 정밀하게 캡처한다. 이러한 방식은 Passive Facial Capture System이 조명 조건에 덜 민감하며, 연구자들에게 더 넓은 실험 범위과 유연성을 제공한다. 또한 복잡한 장비, 특수한 설정 없이도 얼굴의 디테일을 캡처할 수 있기에 시스템 구축에 있어 비용 효율성과 휴대성이 크게 향상된다. 더 나아가 고속 촬영과 조명 동기화의 필요성을 제거함으로써, 동적인 얼굴 표정을 캡처하는데 있어 시스템 확장성을 높일 수 있다. 이러한 점들은 Passive Facial Capture 방식이 Active Facial Capture 방식의 유용한 대안이 될 수 있음을 시사한다. 이에 Passive Facial Capture System 선생연구를 살펴보면, Beeler는 SLR 카메라 7대와 스테레오 카메라 1대 그리고 주변광을 활용한 Passive Facial Capture 시스템을 구성하고, 하이패스 필터를 통해 '어두운 픽셀이 더 깊다' 라는 가정으로 디지털 휴먼 얼굴 외형을 재구성하는 방법론을 제안해 Active Facial System과 동일한 성능을 재현한다[23]. 다만, 특수한 조명을 사용하지 않아 피부의 반사율과 스페큘러 데이터를 얻을 수 없어 피부 표현력의 한계가 있다. 더 나아가 Vagaerts는 두 개의 카메라를 활용해 스테레오 정보를 획득하고, 디지털 휴먼 얼굴 외형을 재구성하는 방법론을 제안하여, 경량화된 시스템과 제어되지 않는 환경에서도 페이셜 캡처가 가능하다는 장점이 있다[24]. 
Active Facial Capture 방식과 동일하게 Passive Facial Capture 방식 역시 얼굴의 표정을 동적으로 표현하는 연구가 진행되었다. 이 중 Bradley는 마커, 페이스 마커, 구조적인 조명에 의존하지 않고 다수의 카메라와 균일한 조명만으로 시간에 따라 변화된 고해상도의 얼굴 외형을 재구성하는 방법론을 제안했다[25]. 하지만 이 방법론은 피사체가 빠르게 움직일 경우 모션 블러와 부정확한 옵티컬 플로우로 인해 지오메트리 재구성에 한계까 존재한다. 이에 이를 극복하고자 Beeler는 페이셜 스캔 시퀀스 데이터에서 기준점으로 활용할 수 있는데 앵커 프레임 개념을 도입해 동적인 얼굴 표정을 표현할 때 재구성된 얼굴 지오메트리의 품질을 개선하고자 한다[26]. 이러한 앵커 프레임은 기준점 역할을 함으로써 일관되고 높은 품질을 유지할 수 있도록 도와주지만, 시퀀스 내에 페이셜 스캔 데이터를 고해상도로 얻어야한다는 점과 앵커 프레임의 품질에 따라 얼굴 지오메트리 영향을 받는다는 한계가 있다. 최근에는 Gotardo가 혈류에 따른 동적인 피부의 텍스처와 반사율, 노멀 맵과 같은 피부 속성 데이터를 획득할 수 있는 방법론을 통해 얼굴 표정의 동적 움직임을 추정하는 모델을 제시했다[27]. 더 나아가 Riviere는 Single Shot에서 교차 편광과 평행 편광을 사용하는 방식으로 피부 반사율을 추정할 수 있으며, 동적인 얼굴 표정을 캡처하기 위해 번거로운 피사체의 움직임이 필요없는 방법론을 제안했다[10].

#### Digital Twin

디지털 트윈이라는 개념은 물리적 공간의 특성을 정밀하게 반영한 가상공간을 생성하고, 이 가상공간에서 물리적 공간의 데이터를 기반으로 다양한 시뮬레이션을 수행함으로써, 데이터 분석과 최적화 방안을 도출한 후에 이를 다시 실제 물리적 공간에 적용하는 방법론으로 이해할 수 있다[28]. 이는 가상공간의 시뮬레이션을 통해 물리적 공간에서 발생 가능한 위험 요소 및 문제를 사전에 파악해 예방하고 문제 해결에 드는 비용을 절감할 수 있다. 디지털 트윈의 개념은 Grieves가 '제품 수명주기 관리'의 과정에서 물리적 제품, 가상 제품, 그리고 이 두가지 요소를 연결하는 링크로 구성된 개념으로 처음 제시되었다[29]. 이러한 디지털 트윈의 초기 개념은 기술적 한계로 인해 충분히 구체화되지 못하였지만, 최근 실시간 데이터 처리 기술과 IoT 기술의 발전에 힘입어 디지털 트윈은 급속한 성장을 이루게 되었다. [Figure 1]에서 연도별로 관찰된 디지털 트윈 연구 추이를 분석해보면, 최근 몇년동안 디지털 트윈에 대한 연구가 폭발적으로 증가하고 있음을 알 수 있다[30]. 이러한 추세는 2012년 NASA에서 디지털 트윈 개념을 재해석해 물리적 모델과 실시간 센서 데이터를 활용한 초고정밀 시뮬레이션 개념으로 정의하여 항공우주 산업에 적용한 것이 큰 계기가 되었다[31].

![](https://i.imgur.com/HEgDYdx.jpg)

선행연구자들이 제시한 디지털 트윈에 대한 다양한 정의를 살펴보면, 크게 가상공간에서의 시뮬레이션을 통한 문제 해결과 물리적 공간과 가상공간의 연결성에 중점을 둔 두 가지의 주장으로 구분될 수 있다. 우선, 디지털 트윈을 시뮬레이션을 통한 문제 해결로 바라보는 연구자들은 디지털 트윈이 실제 데이터와 전문 지식을 기반으로 가상공간에서 보다 정확한 시뮬레이션을 구현하는 것이라고 강조한다[32],[33]. 반면에, 디지털 트윈의 개념을 물리적 공간과 가상공간의 연결성에 초점을 맞춘 연구자들은 디지털 트윈이 물리적-가상공간을 연결하는 매커니즘이라고 주장한다[34],[35],[36]. 이처럼 디지털 트윈에 대한 정의는 다양한 연구자들에 의해 제시되고 있지만, 최근에는 디지털 트윈을 활용한 산업 사례들이 지속적으로 등장하면서 물리적 공간과 가상공간의 연결성에 중점을 둔 정의로 점차 확립되고 있다. 이에 VanderHorn은 디지털 트윈을 물리적 공간과 가상공간의 데이터를 통한 지속적인 변화로 정의하며, 이를 기존 디지털 모델과 구분한다[37]. 또한 Yin은 디지털 트윈과 시뮬레이션 모델의 차이점을 강조하며, 시뮬레이션이 초기 가정을 바탕으로 미래를 예측하는 것에 반해 디지털 트윈은 현재의 물리적 시스템을 기반으로 예측을 수행한다고 정의한다[38]. 아직까지 디지털 트윈에 대한 국제 표준 정의는 확립되지 않았지만, 선행 연구자들의 의견을 종합해보면, 디지털 트윈은 가상공간의 시스템이 물리적 공간의 시스템의 쌍둥이 역할을 하며 전체 시스템 수명 주기동안 상호작용한다고 정의할 수 있다. 이러한 개념을 기반으로 디지털 트윈 기술은 제조업 분야에서 활용되어 공정 파이프라인의 결함 예측 및 생산 효율성 향상을 도모하고 있다.
디지털 트윈 방법론은 기존 시뮬레이션 방법과 차별화되어, 가상공간에서의 시뮬레이션을 통해 문제점을 예측하고 이를 해결하여 물리적 공간의 시스템을 최적화하는 방법론이다. 따라서 디지털 트윈을 구성하는 것은 기존 시뮬레이션과 다르게 몇 가지 특성을 지니고 있다. 첫 번째, '가상공간이 물리적공간 시스템을 얼마나 정밀하게 반영하는가'로 이 특성은 디지털 트윈 환경의 신뢰성을 결정하는 핵심요소로 가상공간과 물리적 공간에서의 시스템 크기와 프로세스가 일치하는 정도를 말한다[39],[40],[41]. 여기서 프로세스는 시뮬레이션 과정에서 변수 간의 관계를 계산하는 과정으로 디지털 트윈의 가상공간 안에서는 물리 법칙을 기반으로 각 변수의 관계를 설명한다. 두 번째, '물리적 공간과 가상공간 간의 유기적인 상호작용이 가능한가'로 물리적 공간에서는 고성능 센서를 통해 데이터를 획득하고 가상공간에서는 시뮬레이션 및 데이터 분석을 통해 문제 식별 및 해결책을 도출한다[42],[43],[44]. 세 번째, '상호작용이 실시간으로 처리되고 적용하는가'로 이러한 특성은 디지털 트윈으로 발견된 파이프라인의 문제점을 즉각적으로 인식하고 대응할 수 있음을 의미한다. 또한 이를 통해 파이프라인 관리가 보다 효율적으로 이루어질 수 있다. 마지막으로 디지털 트윈 특성으로 확장성이 고려되어야 한다. 확장성은 디지털 트윈 시스템이 다른 디지털 모델 혹은 디지털 트윈 시스템과 결합될 때 기존의 성능이나 기능을 손상시키기 않으면서 결합되는 것을 의미한다[45].

### Digital Twin Configuration

#### Facial Capture System Digital Twin Pipeline
본 연구에서 제안된 파이프라인은 [Figure 2]에서 살펴볼 수 있으며, 디지털 트윈 환경에서 얼굴의 외형 지오메트리를 시뮬레이션을 통해 정량적으로 평가하고, 이를 바탕으로 질적 변수를 최적화하여 물리적 시스템에 적용하는 과정을 거친다. 이는 기존 물리적 공간에서의 파이프라인 대비 결과물의 정성적 평가, 수동적인 질적 변수 조절, 파이프라인 최적화 시간 소요의 한계점을 해결할 수 있는 방안을 제시한다. 파이프라인을 세부적으로 살펴보면, 첫 번째 생성된 디지털 휴먼 얼굴 외형을 정량적으로 평가할 수 있다는 장점을 가지고 있다. 물리적 공간에서의 파이프라인과 다르게 디지털 트윈 환경은 페이셜 캡처 과정에서 기 구축된 디지털 휴먼의 얼굴 외형 데이터를 활용한다. 해당 데이터는 Ground Truth로 활용되어 페이셜 캡처를 통해 재구성된 결과물과 비교할 수 있으며, 정량적 평가를 통해 서로의 유사성을 측정할 수 있다. 두 번째로, 제안된 파이프라인은 실시간 엔진을 활용해 수동적인 질적 변수 조절의 한계를 해결할 수 있다. 실시간 엔진에서 구현된 디지털 트윈 환경은 사용자 인터페이스를 통해 조명, 노출, 카메라 위치, 렌즈 초점 거리 등의 질적 변수를 손쉽게 조작할 수 있으며, 상호작용을 통해 실제 시스템에 적용될 수 있다. 이는 기존의 아티스트 중심의 노동 집약적인 작업 흐름을 개선하며, 다양한 실험 환경을 쉽게 구축하여 결과를 확인하는데 장점을 지닌다. 예로, 페이셜 캡처 디지타이징 시스템에서 렌즈를 변경할 때 물리적 공간에서 적용하려면 시간 비용이 들지만, 디지털 트윈 환경에서의 질적 변수 조절은 시간 비용이 들지 않아 시스템의 실험 환경을 다양한 방향으로 탐색할 수 있다. 세 번째로, 페이셜 캡처 디지타이징 시스템 최적화 시간을 효율적으로 활용할 수 있는데, 앞서 언급한 정량적 평가와 자동화된 질적 변수 조절은 디지털 휴먼 얼굴 생성 효율성을 크게 향상시킬 수 있다. 이는 디지털 트윈 환경에서의 대규모 시뮬레이션을 통해 이전에 아티스트가 고려하지 못했던 실험 변수를 발견하고 이를 통해 시스템을 최적화가 가능하다.

![](https://i.imgur.com/rN33cvF.jpg)

#### Automative Facial Geometry Reconstruction Pipeline
지금까지의 논의를 통해 제안된 파이프라인이 기존의 방식에 비해 여러 이점을 가지고 있음을 확인하였다. 따라서 더 나아가 [Figure 2]에서 가상공간에서 페이셜 캡처된 데이터를 기반으로 얼굴 외형을 재구성하는 자동화 파이프라인을 살펴볼 수 있다. 얼굴 외형을 재구성하는 자동화 파이프라인은 크게 세 단계로 구성되며, 얼굴 스캔 데이터 획득, 얼굴 외형 지오메트리 재구성, 얼굴 외형 지오메트리 변형으로 이루어진다. 첫 번째, 얼굴 스캔 데이터를 획득은 [Figure 3]에서 실시간 엔진을 활용해 구성된 가상공간의 페이셜 캡처 디지타이징 시스템을 통해 이루어진다. 디지털 트윈 환경에서 사용되는 카메라는 총 24대로, 20대는 물리적 공간과 상호작용하는 카메라로 구성되며 나머지 4대는 마커를 인식하는 가상의 카메라로 구성된다. 마커는 재구성된 얼굴 외형 지오메트리의 크기와 3D 공간상의 위치를 결정하는데 활용되며, 지오메트리 품질에 영향을 미치지 않는다.

![](https://i.imgur.com/OsvTlxg.png)

두 번째, 얼굴 외형 지오메트리를 재구성하는 과정은 [Figure 4]에서 보이듯 마커 카메라 4대에서 획득된 이미지 데이터를 통해 결과물의 위치와 스케일을 고정하여 디지털 휴먼 얼굴 외형을 생성한다. 이는 디지털 트윈 환경에서의 다양한 시뮬레이션에서 카메라의 위치, 렌즈 초점거리, 조명 조건 등이 변화하여도 생성된 얼굴 외형 결과물이 일관된 위치와 크기로 생성될 수 있도록 보장한다.
![](https://i.imgur.com/D4gFCDM.png)

세 번째, 얼굴 외형 지오메트리 변형 과정은 생성된 디지털 휴먼 얼굴 외형을 기본 해상도의 지오메트리로 변형하고, 캡처된 피부 텍스처를 변형된 지오메트리에 맞게 수정한다. 일반적으로 페이셜 스캔 데이터를 통해 재구성된 지오메트리는 고해상도의 특성을 가지고 있어, 아티스트가 얼굴 표정 표현을 위한 리그 작업을 진행할 때 최적화된 표현에 한계를 지니게 된다. 따라서 형태는 유지하면서, 적절한 해상도를 가지는 얼굴 외형 지오메트리로 변형하는 작업이 필요하다. 따라서 [Figure 5]와 같이 구성된 카메라를 통해 얻은 4개의 이미지를 활용하여, 얼굴 주요 특징점을 추출한다. 이 과정을 통해 기본 얼굴 외형 모델은 특징점을 기반으로 생성된 결과물의 형태로 변형되게 된다. 이처럼 언급된 두번째, 세번째 단계는 디지털 트윈 환경에서 페이셜 캡처 디지타이징 파이프라인이 어떻게 고해상도의 스캔 데이터를 효율적으로 처리하여 결과물을 생성해내는지 보여준다.

![](https://i.imgur.com/kZI81Bw.png)

#### Facial Geometry Evaluation Pipeline
디지털 트윈 페이셜 캡처 파이프라인을 통해 생성된 디지털 휴먼 얼굴 외형은 Ground Truth와 비교를 통해 지오메트리 유사도를 정량적으로 평가할 수 있다. 지오메트리를 정량적으로 평가하는 전반적인 과정은 [Figure 6]에서 살펴볼 수 있다. 이러한 정량적 평가를 수행하는 방법은 Chamfer Loss, Texture Loss를 활용할 수 있으며, 이는 딥러닝 및 컴퓨터 비전 분야에서 널리 활용되는 손실 함수로 볼 수 있다. 우선 Chamfer Loss는 Ground Truth와 결과물에서 N개의 포인트 클라우드를 샘플링하여 지오메트리 유사도를 측정한다. Texture Loss는 Ground Truth의 텍스처와 생성된 결과물의 텍스처 간의 픽셀 간의 차이를 계산하는 방식으로 계산된다. 이러한 손실함수를 기반으로 한 정량적 평가는 시스템 질적 변수 갱신 과정에 영향을 미치며, 정량적 평가 결과에 따라 카메라의 위치, 렌즈 초점 거리, 조명 상태 등을 조절된다. 따라서 제안된 방법론에서는 Ground Truth와 생성된 디지털 휴먼 얼굴 외형 간의 정량적 평가를 통해 높은 정확도의 질적 변수 조정을 가능하게 하며, 이후 해당 파이프라인을 활용해 인공지능 학습에도 적용할 수 있다. 

![](https://i.imgur.com/tlPKhxu.png)

### Results

#### Simulation Phase Overview
본 연구에서 제안된 디지털 트윈 페이셜 캡처 디지타이징 시스템을 통해 물리적 공간의 시스템을 최적화시키기 위해 [Table 1]과 같이 3가지 단계를 거쳐 최적화를 진행한다. 첫 번째 실험은 디지타이징 질적 변수 중 렌즈 초점거리를 45mm로 설정하고, 카메라를 시스템 내에 무작위로 배치하여 얼굴 외형을 생성한다. 이를 통해 카메라의 배치 영역이 얼굴 외형을 재구성하고 텍스처의 생성 품질에 어떠한 영향이 미치는지 분석한다. 첫 번째 실험은 약 4000번 정도의 시뮬레이션으로 구성되었고 이 중 얼굴 외형이 재구성된 것은 약 1100번 정도로 살펴볼 수 있다. 두 번째 실험은 최적의 카메라 위치에서 24mm, 45mm, 60mm, 90mm 렌즈 초점거리를 조합해 도출된 결과물을 정량적으로 평가해 렌즈 초점거리가 얼굴 외형을 재구성하는데 어떠한 영향을 미치는지 살펴본다.

![](https://i.imgur.com/s6QI9zF.png)

#### Camera Zone Simulation
해당 실험은 제한된 수의 카메라로 페이셜 캡처 디지타이징 시스템을 구성하는 데 있어, 영역 별 카메라 배치를 최적화하며 효율적인 파이프라인을 설계하는데 중점을 둔다. 본 연구에서 카메라의 영역 배치에 대한 시뮬레이션을 통해 얻은 데이터를 분석한 결과 [Figure 6]와 같은 결과를 얻을 수 있었다. 이는 카메라가 페이셜 캡처 디지타이징 시스템의 중심을 기준으로 주로 어느 위치에 배치되었는가를 통해 얼굴 외형 지오메트리 재구성 가능성을 나타낸다. 예로, 오른쪽과 왼쪽 영역에 배치된 카메라의 개수 차이가 N개일 때, 오른쪽 영역에 N개 많다면 N, 왼쪽 영역에 많다면 -N으로 표시된다. 마찬가지로 상단과 하단 영역에 배치된 카메라의 개수 차이가 N개일 때, 상단 영역에 N개 많다면 N, 하단 영역에 N개 많다면 -N으로 표시된다. 이를 통해 해당 그래프를 살펴보면, 지오메트리 생성 가능 여부에 따라 시각적으로 표현되는 것을 알 수 있다. 왼쪽은 재구성이 되지 않은 그래프로 산발적으로 퍼져 있는 형태의 패턴을 보이고 있다. 반면에 오른쪽 재구성이 가능한 그래는 주로 -1에서 1사이의 값에 대칭적으로 나타나고 있다. 따라서 페이셜 스캔 데이터를 통해 얼굴 외형 지오메트리를 생성하기 위해서는 카메라의 배치가 대칭적으로 이루어져야함을 알 수 있다.  

![](https://i.imgur.com/d69GMp8.png)

카메라 영역의 최적화를 위해 지오메트리가 생성가능한 데이터에서 Ground Truth와 얼마나 유사한 형태로 생성되었는지 판단할 수 있다. [Figure 7]은 카메라의 수평 및 수직 배치 비율을 기준으로 생성된 지오메트리와 Ground Truth 간의 비교 수치를 시각적으로 표현한 것이다. 해당 그래프에서는 Loss 값이 다소 산발적으로 분포되어 있지만, Loss 값이 최소가 되는 데이터를 살펴보면 수평과 수직 배치에서 대칭적인 형태를 가지고 있음을 알 수 있다. 더 나아가 수직 배치 비율에서는 하단에 비해 상단에 1개의 카메라가 더 많이 배치 될 때 Loss 값이 최소가 되는 것을 볼 수 있다.
![](https://i.imgur.com/T8mpBQe.png)

더 나아가 [Figure 8]에서 수평 및 수직 기준으로 중앙 영역에 배치된 카메라의 개수와 Loss 간의 관계를 분석할 수 있다. 해당 그래프에서는 수평 기준으로 중앙 영역에 9대의 카메라가 배치될 때 최소의 Loss 값을 보이는 것을 확인할 수 있었고, 수직 기준으로는 중앙 영역에 6대의 카메라가 배치될 때 최소의 Loss 값을 나타내는 것을 볼 수 있다. 따라서 종합적으로 [Figure 9]과 같은 카메라 영역 배치 결과를 얻을 수 있었다.

![](https://i.imgur.com/cqZVlMO.png)

![](https://i.imgur.com/VIbydm0.png)


#### Lens Field of View Simulation
해당 실험은 렌즈 초점거리를 조합해 얼굴 외형 이미지 데이터를 획득하는 시뮬레이션을 수행한다. 일반적인 VFX 스튜디오에서는 동일한 렌즈 초점거리를 사용하는 것이 일반적이나 본 연구에서는 다양한 렌즈의 조합 구성에 따라 어떠한 결과가 도출되는지 살펴보려고 한다.

##### 24mm+45mm Simulation
45mm 렌즈를 주 렌즈로 활용하고 24mm 렌즈를 보조 렌즈로 사용하며, 보조 렌즈의 개수가 증가 추이에 따라 어떻게 변화되는지 살펴보고자 한다. [Figure 10]은 24mm 보조 렌즈의 증가 추이에 따른 Chamfer Loss, Texture Loss, 두 손심함수를 더한 것으로 구성된다. Loss 변화 추이를 보면 24mm 렌즈의 개수가 증가함에 따라 Loss가 감소하는 추세를 보이다가, 9개 이후로는 다시 Loss가 상승하는 것을 확인할 수 있다. Chamfer Loss, Texture Loss를 살펴보면, 24mm 렌즈를 많이 사용할수록 넒은 화각의 얼굴 이미지 데이터를 획득할 수 있어 Ground Truth와 유사한 지오메트리를 생성할 수 있지만, 9개 이상 사용할 경우 왜곡으로 인한 지오메트리 변형이 발생하는 것을 알 수 있다. 이러한 결과 24mm 렌즈의 적절한 활용이 얼굴 외형 지오메트리를 생성하는데 기여할 수 있음을 알 수 있었다. 하지만, 과도한 활용은 오히려 왜곡과 정보 손실을 일으켜 지오메트리 품질을 저하시킬 수 있다는 점을 고려해야 한다.
![](https://i.imgur.com/t52Dgcr.png)

##### 45mm+60mm Simulation
해당 실험에서는 45mm 렌즈를 주 렌즈, 60mm 렌즈를 보조 렌즈로 조합해 시뮬레이션을 수행하였다. 분석 결과는 [Figure 11]에서 살펴볼 수 있으며, 역시 60mm 보조 렌즈의 개수에 증가에 따라 Loss 변화 추이를 나타낸다. 그래프를 통해 확인할 수 있듯이 60mm 렌즈가 10에서 11개 사용되는 것을 전후로 Loss가 증가하는 경향을 보인다. Chamfer Loss, Texture Loss를 살펴보면, 60mm 렌즈의 개수가 증가하면서 디테일한 페이셜 캡처 이미지를 얻을 수 있어 Loss가 감소하지만 주 렌즈 개수를 넘어서는 순간 대부분의 이미지의 겹침이 줄어들어 이미지의 재구성이 일어나지 않는 것을 알 수 있다. 또한 Chamfer Loss에 비해 Texture Loss가 큰 변화 폭을 보이는 것은 생성된 지오메트리가 왜곡되며, 텍스처 역시 동일하게 왜곡되기 때문이다. 이러한 분석을 통해 본 연구는 다양한 렌즈 조합과 이에 따른 카메라 배치가 디지타이징 시스템 성능에 어떠한 영향을 미치는지 살펴볼 수 있었고, 시스템 성능을 극대화하는 방안을 제시할 수 있다.
![](https://i.imgur.com/vP7kEcS.png)

##### 45mm+90mm
해당 실험은 45mm 렌즈를 주 렌즈, 90mm 렌즈를 보조 렌즈로 조합해 시뮬레이션을 수행했다. 분석 결과 [Figure 12]에서 보는 것과 같이 90mm 렌즈를 9개 사용한 시점으로 Loss의 상승이 뚜렷하게 관찰되었고, 이는 24mm와 60mm 렌즈를 사용했을 때보다 더욱 명확한 경향을 보였다. 90mm 렌즈의 활용은 확대된 이미지 데이터를 통해 얼굴 지오메트리 및 텍스처 유사도에 큰 변화를 가져왔다. 이러한 결과는 90mm 렌즈를 통해 얻어진 확대된 이미지 데이터가 얼굴 외형의 특징점 겹침 영역이 줄어들어 Ground Truth와 유사한 지오메트리 생성에 어려움이 있다는 것을 시사한다.

![](https://i.imgur.com/qM1MaHl.png)

### Discussion
본 연구는 디지털 트윈을 통해 페이셜 캡처 디지타이징 시스템 파이프라인을 개선하고 최적화하는 방향으로 진행된다. 디지털 트윈을 중심으로 한 본 연구는 기존 물리적 공간의 파이프라인이 가지고 있던 여러 한계점들을 효과적으로 극복함으로써, 높은 효율성과 정량적 평가를 통해 결과를 도출할 수 있는 새로운 접근법을 제시한다. 첫 번째로, 제안된 방법론은 물리적 공간의 다양한 특성들을 정밀하게 반영한 가상공간에서의 조작을 통해 기존의 노동집약적이고 수동적인 수정 과정을 크게 단순화시킨다. 두 번째로, 생성된 디지털 휴먼 얼굴 외형의 정량적 평가를 통한 질적 변수 자동화로 파이프라인 최적화에 소요되는 시간과 비용을 현저히 감소시킨다. 세 번째로, 디지털 트윈을 활용한 광범위한 시뮬레이션은 불필요한 장비 구입을 최소화하고, 기존의 시스템을 재사용 가능하게 함으로 전반적인 비용을 절감하는 효과를 가져온다. 따라서 본 연구에서는 제안된 파이프라인을 활용해 시뮬레이션을 통해 최적화한 결과 카메라의 영역 배치가 지오메트리 및 텍스처 생성 품질에 미치는 영향을 파악할 수 있었다. 특히 대칭적인 형태의 카메라 배치가 고품질의 얼굴 외형 생성에 유리함을 확인하였다. 또한 다양한 렌즈의 조합을 통해 주 렌즈와 보조 렌즈 개수에 따라 결과물 품질에 미치는 영향을 분석할 수 있었다.
따라서 본 연구를 종합적으로 살펴보면, 디지털 트윈을 활용한 페이셜 캡처 디지타이징 시스템 파이프라인 최적화를 통해 VFX 산업에 중요한 기대효과를 제시할 수 있다. 특히 제안된 디지털 트윈 파이프라인 방법론은 VFX 산업의 작업 흐름과 품질에 긍정적인 영향을 미칠 것으로 예상된다. 미시적인 측면에서, 본 연구는 기존의 수작업과 시행착오를 기반으로 한 방법론에 비해 높은 정확도와 효율성을 제공할 것으로 기대된다. 또한 방대한 양의 시뮬레이션 데이터와 자동화된 파이프라인을 통해 빠른 피드백과 결과물의 수정이 가능해 프로젝트 시간과 비용을 절감시킬 수 있다. 거시적 측면에서는, 디지털 트윈 파이프라인이 VFX 산업 전반에 걸쳐 작업 흐름의 효율성을 높이고, 결과물 품질을 향상시키는 데 기여할 것으로 예상된다. 
향후 연구 방향으로는 디지털 트윈 환경을 구성 시에 가상공간의 조명 특성으로 인해 물리적 공간과 일치되는 환경을 제작하는데 한계가 있었다. 따라서 향후에는 DMX 프로토콜 확장을 통해 조명 특성을 더욱 정밀하게 반영하는 방안을 모색할 예정이다. 또한 현재 구성된 디지털 트윈 모델의 경우 아직 중간정도의 성숙도에 머물러 있음에 성숙도를 높이는 방향으로 연구가 진행될 필요가 있다. 특히 시뮬레이션을 통해 생성된 데이터와 Loss를 기반으로 강화학습을 도입함으로 디지털 트윈의 성숙도를 한 단계 더 끌어올릴 수 있을 것으로 예상된다.

[1] Debevec, P., Haukins, T., Tchou, C., Kuiker, H. P., Sarokin, W., Sagar, M.: Acquiring the reflectance field of a human face. In Proceedings of the 27th annual conference on Computer graphics and interactive techniques. pp. 145-156. 2000.
[2] Nehab, D., Rusinkiewicz, S., Davis, J., Ramamoor-thi, R.: Efficiently combining positions and normals for precise 3d geometry. ACM Transaction Graph. pp. 536-543. 2005.
[3] Alexander, O., Rogers, M., Lambeth, W., Chiang, M., Debevec, P.: The Digital Emily Project: Photoreal facial modeling and animation. ACM SIGGRAPH 2009 Course. pp.1-15. 2009.
[4] Mori, M.: The Uncanny Valley, Energy, 7(4), pp.33-35, 1970.
[5] Fyffe, G., Jones, A., Alexander, O., Ichikari, R., Debevec, P.: Driving High-Resolution Facial Scans with Video Performance Capture. University of Southern California Los Angeles. 2014.
[6] Garrido, P., Valgaerts, L, Wu, C., Theobalt, C.: Reconstructing Detailed Dynamic Face Geometry from Monocular Video. ACM Transaction Graph. 32(6).
[7] Cao, C., Bradley, D., Zhou, K., Beeler, T.: Real-Time High-Fidelity Facial Performance Capture. ACM Transactions on Graphics. 29(4). pp.1-9. 2015.
[8] Ichim, A. E., Bouaziz, S., Pauly, M.: Dynamic 3D Avatar Creation from Hand-Held Video Input. ACM Transaction on Graphics. 34(4). pp.1-14. 2015.
[9] Azinovic, D., Maury, O., Hery, C., NieBner, M., Thies, J.: High-Res Facial Appearance Capture from Polarized Smartphone Images. arXiv preprint. 2022.
[10] Rivere, J., Gotardo, P., Bradley, D., Ghosh, A., Beeler, T.: Single-Shot High Quality Facial Geometry and Skin Appearance Capture. ACM Transaction on Graphics. 39(4). pp.1-12. 2020.
[11] Xu, Y., Riviere, J., Zoss, G., Chandran, P., Bradley, D., Gotardo P.: Improved Lighting Models for Facial Appearance Capture. 2022.
[12] Tao, F., Zhang, H., Liu, A., Nee, A. Y.: Digital Twin in Industry: State-of-the-art. IEEE Transcations on Industrial Informatics. 15(4). pp.2405-2415. 2018.
[13] Weyrich, T., Matusik, W., Pfister, H., Bickel, B., Donner, C., Tu, C., McAndless, J., Lee, J., Ngan, A., Jesen, H. W., Cross, M.: Analysis of Human Faces using a Measurement-based Skin Reflectance Model. ACM Transactions on Graphics. 25(3), pp.1013-1024. 2006.
[14] Ma, W. C., Hawkins, T., Peers, P., Chabert, C. F., Weiss, M., Debevec, P. E.: Rapid Acquisition of Specular and Diffuse Normal Maps from Polarized Spherical Gradient Illumination. In Proceedings of the 18th Europraphics Conference on Rendering Techniques. pp.183-194. 2007.
[15] Ghosh, A., Hawkins, T., Peers, P., Frederisksen, S., Debevec, P.: Practical Modeling and Acquisition of Layered Facial Reflectance. ACM Transaction on Graphics. 27(5). pp.1-10. 2008.
[16] Fyffe, G., Graham, P., Tunwattansapong, B., Ghosh, A., Debevec, P.: Near-Instant Capture of High-Resolution Facial Geometry and Reflectance. Computer Graphics Forum. 35(2). pp.353-363. 2016.
[17] Debevec, P., Hawkins, T., Tchou, C., Duiker, H. P., Sarokin, W., Sagar, M.: Acquring the Reflectance Field of a Human Face. In Proceeding of the 27th annual conference on Computer graphics and Interactive techniques ACM Press/Addison-Wesley Publishing Co., ACM. pp.145-156. 2000.
[18] Hawkins, T., Wenger, A., Tchou, C., Gardner, A., Goransson, F., Debevec, P.: Animatable Facial Reflectance Fields. In Proceedings of the Fifteenth Eurographics Conference on Rendering. pp.309-319. 2004.
[19] Wenger, A., Gradner, A., Tchou, C., Unger, J., Hawkins, T., Debevec, P.: Performance Relighting and Reflectance Transformation with Time-Multiplexed Illumination. ACM Transactions on Graphics. 24(3). pp.756-764. 2005.
[20] Nagano, K., Fyffe, G., Alxander, O., Barbic, J., Li, H., Ghosh, A., Debevec, P.: Skin Microstructure Deformation with Displacement Map Convolution. ACM Transactions on Graphics. 34(4). p. 109. 2015.
[21] Fyffe, G., Debevec, P.: Single-Shot Reflectance Measurement from Polarized Color Gradient Illumination. In 2015 International Conference on Computational Photography. pp.1-10. 2015.
[22] Meka, A., Hane, C., Pandey, R., Zollhofer, M., Fanello, S., Fyffe, G., Kowdle, A., Yu, X., Busch, J., Dourgarian, J.: Deep Reflectance Fields: High-Quality Facial Reflectance Field Inference from Color Gradient Illumination. ACM Transaction on Graphics. 38(4). pp.1-12. 2019.
[23] Beeler, T., Bickel, B., Beardsley, P., Sumner, B., Gross, M.: High-Quality Single-Shot Capture of Facial Geometry. ACM Transactions on Graphics. 29(3). pp.1-9. 2010.
[24] Vagaerts, L., Wu, C., Bruhn, A., Seidel, H. P., Theobalt, C.: Lightweight Binocular Facial Performance Capture under Uncontrolled Lighting. ACM Transactions on Graphics. 31(6). pp.1-11. 2012.
[25] Bradley, D., Heidrich, W., Popa, T., Sheffer, A.: High Resolution Passive Facial Performance Capture. ACM SIGGRAPH 2010 papers. pp.1-10. 2010.
[26] Beeler, T., Hahn, F., Bradley, D., Bickel, B., Bearsdsley, P., Gotsman, C., Sumner, R. W., Gross, M.: High-Quality Passive Facial Performance Capture using Anchor Frames. ACM Transactions on Graphics. 30(4). pp.1-10. 2011.
[27] Gotardo, P., Riviere, J., Bradley, D., Ghosh, A., Beeler, T.: Practical Dynamic Facial Appearance Modeling and Acquisition. ACM Transactions on Graphics. 37(6). pp.1-13. 2018.
[28] Evolution & Transformation Research Institute, Digital Twin Technique Report. 2021.
[39] Grieves, M.: Digital Twin: Manufacturing Excellence through Virtual Factory Replication. White Paper. 2014.
[30] Tao, F., Zhang, H., Liu, A., Nee, A. Y. C.: Digital Twin in Industry: State-of-the-art. IEEE Transaction on Industrial Informatics. 14(4). pp.2405-2415. 2019.
[31] Glaessagen, E., Stargel, D.: The Digital Twin Paradigm for Future NASA ans U.S. Air Force Vehicles. In 53rd AIAA/ASME/ASCE/AHS/ASC structures, structural dynamics and materials conference 20th AIAA/ASME/AHS adaptive structures conference 14th AIAA. pp.1818. 2012.
[32] Weyer, S., Meyer, T., Ohmer, M., Gorecky, D., Zuhlke, D.: Future Modeling and Simulation of CPS-based Factories: An Example from the Automotive Industry. IFAC PapersOnline. 49(31). pp.97-102. 2016.
[33] Gabor, T., Belzner, L., Kiermeier, M., Beck, M. T., Neitz, A.: A Simulation-based Architecture for Smart Cyber-Physical System. In Proceeding IEEE International Conference Autonomic Computer. pp.374-379. 2016.
[34] Qi, Q. L., Tao, F.: Digital Twin and Big Data Towards Smart Manufacturing and Industry 4.0: 360 Degree Comparison. IEEE Access. 6. pp.3585-3593. 2018.
[35] Tao, F., Zhang, M., Cheng, J. F., Qi, Q. L.: Digital Twin Workshop: A New Paradigm for Future Workshop. Computer Integration Manufacturing System. 23(1). pp.1-9. 2017.
[36] Tao, F., Liu, W., Liu, J., Liu, X., Qu, T.: Digital Twin and its Potential Application Exploration. Computer Integrated Manufacturing Systems. 24(1). pp.1-18.
[37] VanDerHorn, E., Sankaran, M.: Digital Twin: Generalization, Characterization and Implementation. Decision Support System. 145. 2021.
[38] Yin, C., McKay, A.: Introduction to Modeling and Simulation Techniques. In Proceedings of ISCIIA 2018 and ITCA 2018. Leads. 2018.
[39] Reifsnider, K., Majumdar, P.: Multiphysics Stimulated Simulation Digital Twin Methods for Fleet Management. In 54th AIAA/ASME/ASCE/AHS/SC Structures, Structural Dynamics, and Materials Conference. pp.1578. 2013.
[40] Grieves, M., Vickers, J.: Digital Twin: Mitigating Unpredictable, Undesirable Emergent Behavior in Complex Systems. Transdisciplinary Perspectives on Complex Systems: New Findings and Approaches. pp.85-113. 2017.
[41] Alam, K. M., EI, Saddik, A.: C2PS: A Digital Twin Architecture Reference Model for the Cloud-based Cyber-Physical Systems. IEEE Accessed. 5. pp.2050-2062. 2017.
[42] Abramovici, M., Gobel, J. C., Savarino, P.: Reconfiguration of Smart Products during their Use Phase based on Virtual Product Twins. CIRP Annals. 66(1). pp.165-168. 2017.
[43] Demkovich, N., Yablochnikov, E., Abaev, G.: Multiscale Modeling and Simulation for Industrial Cyber-Physical Systems. In 2018 IEEE Industrial Cyber-Physical Systems. pp.291-296. 2018.
[44] Schleich, B., Anwer, N., Mathieu, L., Wartzack, S.: Shaping the Digital Twin for Design and Production Engineering. CIRP annals. 66(1). pp.141-144. 2017.
[45] Sun, W., Ma, W., Zhou, Y., Zhang, Y.: An Introduction to Digital Twin Standards. GetMobile: Mobile Computing and Communications. 26(3). pp.16-22. 2022.