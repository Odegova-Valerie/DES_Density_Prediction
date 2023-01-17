# DES_Density_ML_Prediction
## 1. Описание проекта
**Глубокие эвтектические растворители (ГЭР, DES)** представляют собой новый класс многокомпонентных смесей, характеризующихся пониженной температурой плавления по сравнению с чистыми исходными веществами. Они зарекомендовали себя как эффективные экстрагенты для органического синтеза, нефтехимии и целлюлозно-бумажной промышленности. Для проектирования технологического процесса необходимо знание всех физико-химических характеристик такой смеси. Плотность является наиболее важной характеристикой, влияющей на сольватационную способность DES, что может сказываться на эффективности экстракции. 
Несмотря на то, что большинство задач до сих пор решаются эмпирическим путем, доказана эффективность предсказания физико-химических характеристик с помощью термодинамического моделирования и алгоритмов машинного обучения.

В данной работе была собрана база данных по плотности DES, содержащая более 4000 строк. Для предсказания плотности с помощью машинного обучения были использованы геометрические и экспериментальные дескрипторы, а также фингерпринты смесей. Самыми эффективными моделями машинного обучения оказались бустинги (XGBoosting Regression
Cat Boosting Regression). Для кросс-валидации R2 = 0.81, a RMSE = 0.06.

![image](https://user-images.githubusercontent.com/101416592/212757015-c112dba0-a9a2-4f4f-9a5a-aa2a6c479b2b.png)

## 2. 

