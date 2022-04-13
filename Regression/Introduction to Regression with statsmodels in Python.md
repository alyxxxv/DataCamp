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

adding a linear trend line
``` python
# Draw a trend line on the scatter plot of price_twd_msq vs. n_convenience
sns.regplot(x="n_convenience",
         y="price_twd_msq",
         data=taiwan_real_estate,
         ci=None,
         scatter_kws={'alpha': 0.5})

# Show the plot
plt.show()
```

Straight Line atau garis lurus dibedakan menjadi 2. 
1. Intercept : ketika nilai y ketika berada x = 0
2. Slope : kecuraman dari garis. persamaannya adalah y = intercept + slope*x

untuk running model linear regression. 

``` python
from statsmodels.formula.api import ols
mdl_payment_vs_claims = ols("total_payment ~ n_class", data=swedish_motor_insurance

mdl_payment_vs_claims=mdl_payment_vs_claims.fit()
print(mdl_payment_vs_claims.params)
```

**Categorical explanatory variables**

Visualizing 1 numeric and 1 categorical variable 

``` python
#membuat grafik histogram berdasarkan data kategorikal
import matplotlib.pyplot as plt
import seaborn as sns

sns.displot(data=fish, x="mass_g", col="species", col_wrap=2,bins=9)
plt.show()
```
<img width="204" alt="2022-04-13_20h06_42" src="https://user-images.githubusercontent.com/87213160/163187076-9a64fa76-7dd9-47fc-b2ca-f4985c05ce38.png">

``` python
#SUMMARY STATISTICS MEAN MASS BY SPECIES
summary_stats =fish.groupby("species")["mass_g"].mean()
print(summary_stats)
```
