# DES_Density_ML_Prediction
## 1. Описание проекта
**Глубокие эвтектические растворители (ГЭР, DES)** представляют собой новый класс многокомпонентных смесей, характеризующихся пониженной температурой плавления по сравнению с чистыми исходными веществами. Они зарекомендовали себя как эффективные экстрагенты для органического синтеза, нефтехимии и целлюлозно-бумажной промышленности. Для проектирования технологического процесса необходимо знание всех физико-химических характеристик такой смеси. Плотность является наиболее важной характеристикой, влияющей на сольватационную способность DES, что может сказываться на эффективности экстракции. 
Несмотря на то, что большинство задач до сих пор решаются эмпирическим путем, доказана эффективность предсказания физико-химических характеристик с помощью термодинамического моделирования и алгоритмов машинного обучения.

В данной работе была собрана база данных по плотности DES, содержащая более 4000 строк. Для предсказания плотности с помощью машинного обучения были использованы геометрические и экспериментальные дескрипторы, а также фингерпринты смесей. Самыми эффективными моделями машинного обучения оказались бустинги (XGBoosting Regression
Cat Boosting Regression). Для кросс-валидации R2 = 0.81, a RMSE = 0.06.

![image](https://user-images.githubusercontent.com/101416592/212757015-c112dba0-a9a2-4f4f-9a5a-aa2a6c479b2b.png)

## 2. База данных
Файл DES database.xlsx содержит полную базу данных о названиях, молярном составе, типе DES, плотности, а также температуре, при которой измерялась плотность. Ссылки на статьи в данной базе не добавлены, так как позже будут использоваться для научной публикации

## 3. Описание jupiter notebooks
### 3.1. 1_OVS_DA_Density
В данном jupiter notebook проводится первичная обработка данных, очистка от сомнительных значений, перевод названий химических соединений в SMILES, очистка от повторов, а также проведен Разведочный анализ данных (EDA) для дальнейшего добавления дескрипторов и машинного обучения

### 3.2. 2_OVS_Density_Descriptors
В данном jupiter notebook происходит добавление различных дескрипторов в базу данных, полученную в 1_OVS_DA_Density, добавляются геометрические дескрипторы, отвечающие за форму молекулы, количества структурных фрагментов, а также фингерпринты (вектора чисел, описывающие структурный состав молекулы). Геометрические и экспериментальные дескрипторы были усреднены для двух и трех молекул, входящих  в состав DES, с учетом мольных соотношений. Чтобы избежать переобучения база данных была очищена от коррелирующих дескрипторов. Для построения моделей машинного обучения были выбраны геометрические и экспериментальные дескрипторы, а также фингерпринты. Также в данном файле описаны все аспекты работы с данными в проекте.

### 3.3. 3_OVS_Density_MO
В данном jupiter notebook происходит предсказание плотности на основе базы данных, полученной в 2_OVS_Density_Descriptors, проводится разделение на train и test с учетом компонентов, входящих в систему. Были использованы линейная регрессия, деревья решений, бустинги, метод опорных векторов, метод К блидайших сосоедей. Для каждой модели были оптимизированы гиперпараметры и посчитаны метрики для тренировочного датасета и кросс-валидации, наиболее эффективными оказались бустинги.


## 4. Общие выводы по работе с данными
**Какие источники данных?**
Данные были собраны из литературных статей по данный тематике, всего около 4500 строк. Данные были собраны в ручную, в связи с различным оформлением научных статей.

**Какое качество и полнота данных?**
Журналы были выбраны с высоким импакт-фактором, данные в основном были полные, то есть содержали значение плотности, названия компонентов, их мольных долей, а также температуры, при которой проводилось исследование.

**Как увеличить объем и качество ваших данных?**
Собранная база данных содержит полные и качественные данные, которые можно натйи на данный момент. Основной пролемой работы с данными была их несбалансированность (Разные типы DES в базе данных представлены в разном объеме ввиду их разной популярности среди исследователей. Для решения данной проблемы были использованы оверсэмплинг и применение весов при машинном обучении. Веса показали хороший результат, поэтому объем данных было решено не увеличивать за счет оверсэмплинга.
 
**Как данные влияют на результат вашего проекта?**
Данные используются для моделей машинного обучения для предсказания плотности DES. Их качество и количество напрямую связано с эффективностью моделей.

