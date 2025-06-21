Diabetni aniqlash: Random Forest + SMOTEENN + GridSearchCV

Bu loyiha mashinaviy o'qitish asosida diabet kasalligini aniqlashga qaratilgan bo'lib, kuchli model — Random Forest yordamida 90% 
dan ortiq aniqlikka erishdi.

Ma'lumotlar:
Ma'lumotlar diabetes.csv faylidan olingan bo'lib, Pima indians ayollari haqida turli sog'liq ko'rsatkichlarini o'z ichiga oladi:

Glucose(Glyukoza-uzum shakari),

BloodPressure(Qon bosimi),

SkinThickness(teri (yog') qalinligi),

Insulin(insulin-oshqozon osti bezi gormoni,asosi yishi qondagi shakar miqdorini me'yorda ushlash),

BMI(bo'y massa indeksi kg/m2)

Age(yosh),

Pregnancies(Homiladorliklar soni-ayni damgacha necha marta xomilador bo'lganligi)

Outcome (0 = sog'lom, 1 = diabet)(natija)

 Ishlov berish bosqichlari:

Bosqich
Amal
1. Nol qiymatlar:

0 qiymatlar NaN bilan almashtirildi va ustunlarning o'rtacha qiymatlari bilan to'ldirildi.

2. Feature Engineering

Yangi ustunlar: Age * BMI, Glucose / (Insulin+1)

3. Balanslash:

SMOTEENN yordamida klasslar balanslandi.

4. Scaling:

StandardScaler yordamida barcha xususiyatlar normallashtirildi

5. Train-test:

80/20 nisbatda bo'lingan

6. Model:

RandomForestClassifier

7. Optimallashtirish:

GridSearchCV yordamida eng yaxshi parametrlar tanlandi.

  GridSearchCV eng yaxshi parametrlar:

{
  'n_estimators': 200,
  'max_depth': 8,
  'min_samples_split': 2,
  'max_features': 'sqrt'
}

  Model natijalari (Test to'plamida):

Accuracy: 90.1%

Recall (1): 98% → Diabet kasalligini aniqlashda juda yuqori aniqlik.

F1-score (1): 0.91

Confusion Matrix:

[[45,  10]
 [1 , 55]]

45: sog'lomlar to'g'ri aniqlangan

55: diabetlar to'g'ri aniqlangan

Faqat 1 bemor noto'g'ri sog'lom deb baholangan (juda yaxshi natija)

  Grafik tahlillar

Confusion Matrix vizualizatsiyasi:

Feature Importances (modellashtirishda eng muhim ustunlar):

Glucose, BMI, Age, Glucose/Insulin ratio

  Xulosa:
Random Forest modeli — optimallashtirilgan, balanslangan va tibbiy tashxislash uchun ishonchli natijalar ko'rsatdi.

Yaxshi bashorat,

Yuqori recall,

Kengaytirish va tushuntirish oson,

  Kutubxonalar:

pandas, numpy, seaborn, matplotlib
sklearn: GridSearchCV, train_test_split, metrics
imblearn: SMOTEENN
xgboost (agar taqqoslash qilinsa)

Praktikum datasets manbasi: @anvarnarz

 
