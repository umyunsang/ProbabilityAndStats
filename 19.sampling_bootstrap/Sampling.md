
---
### 모집단 통계 추정

우리는 모집단에서 추출된 샘플을 사용하여 모집단의 평균과 분산을 추정하는 방법에 대해 다룰 것입니다. 이를 통해 원래 모집단에 대해 확률적 주장을 할 수 있습니다. 이는 대부분의 과학 분야에서 중요한 요구 사항입니다.

예를 들어, 당신이 부탄의 왕이라고 가정해봅시다. 부탄 국민의 평균 행복도를 알고 싶지만, 모든 사람에게 물어볼 수는 없습니다. 대신, 무작위로 선택된 소표본에게 물어볼 수 있습니다. 다음 섹션에서는 소표본을 기반으로 할 수 있는 원칙적인 주장에 대해 논의할 것입니다. 우리는 무작위로 선택된 200명의 부탄 국민을 샘플로 하여 그들의 행복도를 조사한다고 가정합니다. 우리의 데이터는 다음과 같습니다: 72, 85, ..., 71. 이를 200개의 I.I.D. (독립적이고 동일하게 분포된) 확률 변수 $X_1, X_2, ..., X_n$의 집합으로 생각할 수 있습니다.

## 샘플 이해하기

샘플링의 아이디어는 간단하지만, 세부 사항과 수학적 표기법은 복잡할 수 있습니다. 다음 그림은 관련된 모든 아이디어를 보여줍니다:

![샘플링 그림](https://chrispiech.github.io/probabilityForComputerScientists/img/chapters/samples.png)

이론적으로는 큰 모집단(예: 부탄의 774,000명)이 존재합니다. 우리는 이 모집단에서 무작위로 $n$명의 사람들을 샘플로 수집하며, 모집단의 각 사람은 샘플에 포함될 확률이 동일합니다. 각 사람으로부터 하나의 숫자(예: 그들이 보고한 행복도)를 기록합니다. 우리는 샘플링된 $i$번째 사람의 숫자를 $X_i$라고 부를 것입니다. 샘플 $X_1, X_2, ..., X_n$을 히스토그램으로 시각화할 수 있습니다.

우리는 모든 $X_i$가 동일한 분포를 가진다고 가정합니다. 이는 샘플들이 단일한 분포 $F$에서 추출되었다고 가정하는 것입니다. 이산 확률 변수의 분포는 확률 질량 함수를 정의해야 합니다.

## 샘플에서 평균과 분산 추정

우리는 데이터가 동일한 기저 분포( $F$ )에서 추출된 IID로 가정합니다. 이 분포의 참된 평균( $\mu$ )과 참된 분산( $\sigma^2$ )이 있습니다. 모든 부탄 국민과 이야기할 수 없기 때문에, 우리는 샘플을 통해 평균과 분산을 추정해야 합니다. 샘플에서 샘플 평균( $\overline{X}$ )과 샘플 분산( $S^2$ )을 계산할 수 있습니다. 이 값들은 참된 평균과 참된 분산에 대한 가장 좋은 추정치입니다.


$$\overline{X} = \sum_{i=1}^n \frac{X_i}{n} \quad S^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i - \overline{X})^2$$


첫 번째 질문은, 이러한 추정치가 불편 추정치인지입니다. 불편 추정치란, 이 샘플링 과정을 여러 번 반복할 경우, 우리의 추정치의 기대값이 우리가 추정하려는 참된 값과 같아야 한다는 것을 의미합니다. $\overline{X}$에 대해 불편 추정치임을 증명할 것입니다. $S^2$에 대한 증명은 강의 슬라이드에 있습니다.


$$E[\overline{X}] = E\left[\sum_{i=1}^n \frac{X_i}{n}\right] = \frac{1}{n}E\left[\sum_{i=1}^n X_i\right] = \frac{1}{n}\sum_{i=1}^n E[X_i] = \frac{1}{n}\sum_{i=1}^n \mu = \frac{1}{n}n\mu = \mu$$


샘플 평균 공식은 기대값의 이해와 관련이 있어 보입니다. 샘플 분산도 마찬가지지만, 방정식의 분모에 있는 $(n-1)$는 놀라운 요소입니다. 왜 $(n-1)$일까요? 이 분모는 $E[S^2] = \sigma^2$가 되도록 보정하는 데 필요합니다.

증명의 직관은 샘플 분산이 샘플 평균, 즉 참된 평균이 아니라 샘플 평균에 대한 각 샘플의 거리로 계산된다는 것입니다. 샘플 평균 자체도 변동하며, 그 분산도 참된 분산과 관련이 있습니다.

## 표준 오차

좋습니다. 우리의 평균과 분산 추정치가 불편하다는 것을 납득했습니다. 하지만 이제 샘플 평균이 참된 평균에 비해 얼마나 변동할 수 있는지 알고 싶습니다.


$$\text{Var}(\overline{X}) = \text{Var}\left(\sum_{i=1}^n \frac{X_i}{n}\right) = \left(\frac{1}{n}\right)^2 \text{Var}\left(\sum_{i=1}^n X_i\right) = \left(\frac{1}{n}\right)^2 \sum_{i=1}^n \text{Var}(X_i) = \left(\frac{1}{n}\right)^2 \sum_{i=1}^n \sigma^2 = \left(\frac{1}{n}\right)^2 n \sigma^2 = \frac{\sigma^2}{n}$$

$$\approx \frac{S^2}{n}$$

$$\text{Std}(\overline{X}) \approx \sqrt{\frac{S^2}{n}}$$

이 용어, $\text{Std}(\overline{X})$,는 표준 오차라고 불립니다. 이는 과학 논문에서 평균의 추정치의 불확실성을 보고하는 방법이며, 오차 막대를 계산하는 방법입니다. 이제 부탄 국민의 행복도를 위해 이러한 훌륭한 통계치를 계산할 수 있습니다. 잠깐만요! $\text{Std}(S^2)$를 계산하는 방법을 알려주지 않았습니다. 중앙 극한 정리는 $S^2$의 계산에 적용되지 않기 때문에, 더 일반적인 기술이 필요합니다. 다음 장에서 다룰 부트스트래핑을 참고하세요.

우리의 행복도 샘플이 $n = 200$명이라고 가정해 봅시다. 샘플 평균은 $\overline{X} = 83$ (단위는 무엇인가요? 행복도 점수?)이고, 샘플 분산은 $S^2 = 450$입니다. 우리는 이제 평균 추정치의 표준 오차를 1.5로 계산할 수 있습니다. 결과를 보고할 때 부탄의 평균 행복 점수 추정치가 $83 \pm 1.5$라고 말할 것입니다. 행복도의 분산 추정치는 $450 \pm \, ?$입니다.