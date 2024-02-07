> [!caution] This page contained a drawing which was not converted.   

- **RMS = 0.707** #important
- **V****RMS** **= V** **peak** **/ root(2)**
- **I****RMS** **= I** **peak****/root(2)**
- **V****RMS** **= V** **peak** *** 0.707**

  

**V1 = most significant bit**

**V****out** **= - (V****1** **+ V****2****/2 + V****3****/4 …)**

  

**V****n** **/ 2****n-1** **is general formula**

  
  

|   |   |
|---|---|
|Manchester|0s = high to low|
|(SPLIT)|1s = low to high|

  

|   |   |
|---|---|
|Diff Manchester|0s = high to low|
|(SPLIT)|1s = swap each 1|

  

|   |   |
|---|---|
|NRZ-L|0s = low / below middle|
|(NON-SPLIT)|1s = high / above middle|

  

|   |   |
|---|---|
|NRZ-I|0s = same as the last voltage|
|(NON-SPLIT)|1s = swap directions / above or below|

  

|   |   |
|---|---|
|Return to Zero|0s = low to mid|
|(SPLIT)|1s = high to mid|

  

|   |   |
|---|---|
|Unipolar|0s = none (bottom/zero)|
|(NON-SPLIT)|1s = high (top/power)|

  

|   |   |
|---|---|
|Bipolar|0s = mid (zero)|
|(NON-SPLIT)|1s = swapping from high to low (positive to negative)|