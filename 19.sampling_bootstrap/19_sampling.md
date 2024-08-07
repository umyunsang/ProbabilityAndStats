
---

### 샘플을 통한 모평균과 모분산 추정

샘플을 사용하여 모수(모평균 $\mu$와 모분산 $\sigma^2$)를 추정할 때, 통계적 추정량을 이용하여 가장 좋은 추정치를 제공합니다. 여기서는 200명의 샘플에서 모평균과 모분산을 추정하는 방법에 대해 설명하겠습니다.

#### 모평균 ($\mu$) 추정

1. **$\mu$의 가장 좋은 추정치**:
   - 샘플 $(X_1, X_2, ..., X_n)$이 주어졌을 때, 모평균 $\mu$의 가장 좋은 추정치는 샘플 평균 $\overline{X}$입니다.
   - 샘플 평균 $\overline{X}$는 다음과 같이 정의됩니다:
     $$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$$
	
   - $\overline{X}$는 $\mu$의 불편 추정량으로, $E[\overline{X}] = \mu$입니다.

2. **샘플 평균에 대한 직관**:
   - 중심극한정리에 따르면, 샘플 크기 $n$이 충분히 크면 샘플 평균의 분포는 정규분포에 가까워집니다. 즉, $\overline{X} \sim N(\mu, \sigma^2/n)$입니다.
   - 만약 여러 개의 크기 $n$인 샘플을 여러 번 추출할 수 있다면:
     1. 각 샘플에 대해 샘플 평균을 계산합니다.
     2. 이 샘플 평균들의 평균은 모평균에 가까워집니다.

#### 모분산 ($\sigma^2$) 추정

1. **모분산 ($\sigma^2$)**:
   - 만약 전체 모집단 $(x_1, x_2, ..., x_N)$을 알고 있다면:
     
    $$ \sigma^2 = E[(X - \mu)^2] = \frac{1}{N} \sum_{i=1}^N (x_i - \mu)^2$$
     
   - 그러나, 한 개의 샘플만 가지고 있다면:
     
     $$S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2$$
     
   - $S^2$는 $\sigma^2$에 대한 불편 추정량입니다. 즉, $E[S^2] = \sigma^2$입니다.
   - $\frac{1}{n-1}$는 $S^2$를 불편 추정량으로 만들기 위한 보정 계수로, $S^2$는 자유도 $n-1$의 카이제곱 분포에 따릅니다.

### 샘플 분산 $S^2$에 대한 직관

샘플 분산 $S^2$는 모집단 분산 $\sigma^2$에 대한 불편 추정량입니다. 이를 통해 모집단의 분산을 추정할 수 있습니다. 샘플 분산에 대한 직관을 다음과 같이 설명할 수 있습니다:

1. **샘플 분산의 정의**:
   - 주어진 샘플 $(X_1, X_2, ..., X_n)$에서 샘플 평균 $\overline{X}$는 다음과 같이 정의됩니다:
     $$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$$
     
   - 샘플 분산 $S^2$는 다음과 같이 정의됩니다:
     
     $$S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2$$
     

2. **불편 추정량**:
   - 샘플 분산 $S^2$는 모집단 분산 $\sigma^2$의 불편 추정량입니다. 이는 $S^2$의 기대값이 $\sigma^2$와 같음을 의미합니다:
     
     $$E[S^2] = \sigma^2$$
     
   - 샘플 평균 $\overline{X}$를 이용하여 계산된 분산은 모집단 평균 $\mu$를 사용하여 계산된 분산보다 작게 나옵니다. 따라서, 샘플 분산을 구할 때 $n$ 대신 $n-1$로 나누어 보정합니다. 이를 통해 샘플 분산이 모집단 분산의 불편 추정량이 됩니다.

3. **직관적인 설명**:
   - 모집단의 분산 $\sigma^2$는 모집단 전체의 각 데이터가 평균에서 얼마나 떨어져 있는지를 측정합니다. 그러나 우리는 모집단 전체를 알 수 없기 때문에 샘플을 사용합니다.
   - 샘플을 사용할 때, 샘플 평균 $\overline{X}$는 모집단 평균 $\mu$의 추정치이므로, 샘플의 각 데이터가 샘플 평균에서 얼마나 떨어져 있는지를 측정하는 것이 샘플 분산 $S^2$입니다.
   - $n-1$로 나누는 이유는 샘플의 자유도 때문입니다. 샘플 평균 $\overline{X}$를 이미 계산했기 때문에, 실제로는 $n$개의 데이터 포인트 중 $n-1$개의 데이터 포인트만 독립적으로 변할 수 있습니다. 따라서, $n-1$로 나누어야 샘플 분산이 모집단 분산의 불편 추정량이 됩니다.

### 모집단 통계 추정

1. **샘플 수집**:
   - 샘플 $X_1, X_2, ..., X_n$을 수집합니다. 예: $(72, 85, 79, 79, 91, 68, ..., 71), n= 200$ 

2. **샘플 평균 계산**:
   - 샘플 평균 $\overline{X}$는 다음과 같이 계산됩니다:
     
     $$\overline{X} = \frac{1}{n} \sum_{i=1}^n X_i$$
     
   - 예를 들어, $\overline{X} = 83$

3. **샘플 편차 계산**:
   - 각 샘플 데이터와 샘플 평균의 차이를 구합니다:
     
     $$X_i - \overline{X}$$
     
   - 예: $(-11 \,(72-83), 2 \,(85-83), -4 \,(79-83), -4, 8, -15, ..., -12)$

4. **샘플 분산 계산**:
   - 샘플 분산 $S^2$는 다음과 같이 계산됩니다:
     
     $$S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2$$
     
   - 예를 들어, $S^2 = 793$

### 우리의 추정치 $\overline{X}$와 $S^2$는 얼마나 정확한가?

- $\overline{X}$의 기대값은 모평균 $\mu$와 같습니다:
  
  $$E[\overline{X}] = \mu$$
  
- $\overline{X}$의 분산은 $\sigma^2 / n$입니다:
  
  $$Var(\overline{X}) = \frac{\sigma^2}{n}$$
  

**샘플 평균의 표준 오차**는 $\overline{X}$의 표준 편차에 대한 추정치입니다:

$$SE = \sqrt{\frac{S^2}{n}}$$


**직관적 설명**:
- $S^2$는 모분산 $\sigma^2$의 불편 추정량입니다.
- $\frac{S^2}{n}$는 $\frac{\sigma^2}{n}$, 즉 $\overline{X}$의 분산에 대한 불편 추정량입니다.
- $\sqrt{\frac{S^2}{n}}$는 $\overline{X}$의 분산의 제곱근을 추정할 수 있습니다.

따라서, 샘플 평균 $\overline{X}$와 샘플 분산 $S^2$는 각각 모평균 $\mu$와 모분산 $\sigma^2$에 대한 좋은 추정치를 제공하며, 표준 오차(SE)는 샘플 평균의 변동성을 측정하는 데 사용됩니다.
