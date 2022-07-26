---
layout: post
title: "Breast_Cancer_Classification"
date: 2022-07-26+
categories: Machine_Learning

---
### 위스콘신의 유방암 데이터셋을 사용

## Step 1. Importing Libraries

먼저, 사용할 라이브러리들을 가지고 옵니다.

ln[1] :

```python
import warnings # 각종 경고 메시지를 무시하는 라이브러리
warnings.filterwarnings('ignore')

import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

#### 다음으로는 사용할 데이터 셋을 받아옵니다

ln[2] :

```python
from sklearn.datasets import load_breast_cancer

cancer = load_breast_cancer()
```

## Step 2. EDA

먼저 cancer 데이터셋의 ``type``부터 확인해보겠습니다.

ln[3] :

```python
print(type(cancer))
```

Out[3] :

```python
sklearn.utils._bunch.Bunch
```

Bunch 객체는 딕셔너리와 유사하며, `keys()`를 통해 키 목록을 조회할 수 있습니다.

ln[4] :

```python
cancer.keys
```

Out[4]:

```python
dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
```

`data`는 학습해야 할 데이터입니다.

ln[5] :

```python
print(cancer.data)
```

`target`은 예측할 데이터입니다.

ln[6] :

```python
print(cancer.target)
```

target을 보면, 0과 1로 구성된 Array가 출력됩니다. 이 0과 1이 무엇을 의미하는 지는 `target_name`을 보면 알 수 있습니다.

ln[7] :

```python
print(cancer.target_name)
```

Out[7] :

```python
array(['malignant', 'benign'], dtype='<U9')
```

- 0 : malignant (악성종양)
- 1 : benign (양성종양)

즉, 구성할 모델은 `data`를 보고 `target`값을 예상하는 모델입니다.

`DESCR`은 해당 데이터셋의 전반적인 내용을 보여줍니다.

ln[8] :

```python
print(cancer.DESCR)
```

Out[8] :

```python
.. _breast_cancer_dataset:

Breast cancer wisconsin (diagnostic) dataset
--------------------------------------------

**Data Set Characteristics:**

    :Number of Instances: 569

    :Number of Attributes: 30 numeric, predictive attributes and the class

    :Attribute Information:
        - radius (mean of distances from center to points on the perimeter)
```
