## Introduction to Regression with statsmodels in Python ##

kali ini bakal membahas mengenai regresi. Regresi sendiri merupakan salah satu cara untuk memperoleh hubungan antara data-data. Yang mana, data tersebut terdiri dari data independent dan data dependent. Pertama, perlu diketahui Descriptive statisticsnya terlebih dahulu. Pada kali ini, dapat menggunakan **pandas**. 

data :

<img width="192" alt="2022-04-13_17h03_09" src="https://user-images.githubusercontent.com/87213160/163154653-424a13fc-196a-46a8-b97f-0ad9dff9a533.png">

kodingan ini digunakan untuk mengetahui nilai mean dari suatu data. 
``` python
import pandas as pd
print(swedish_motor_insurance.mean())
```
untuk korelasi dengan dua variabel, maka bisa menggunakan seperti berikut: 
``` python
print(swedish_motor_insurance['n_claims'].corr(swedish_motor_insurance['total_payment_sek']))
```

pada kali ini, terdapat 3 tipe regresi 

1. Linear Regression : digunakan ketika variabel responnya numerik, seperti dalam kumpulan data asuransi kendaraan bermotor
2. logistic regression : digunakan ketika variabel respon logis. 
3. Simple linear/logistic regression

Sebelum memulai menjalankan model regresi, alangkah baiknya dengan memvisualisasikan kumpulan data anda. 

**Visualizing Pairs of Variables**

``` python
import matplotlib.pyplot as plt
import seaborn as sns

sns.scatterplot (x="n_claims", y="total_payment_sek", data=swedish_motor_insurance)

plt.show()
```

adding a linear trend line
``` python
sns.regplot(x="n_claims", y="total_payment_sek", data=swedish_motor_insurance, ci=none)

```



