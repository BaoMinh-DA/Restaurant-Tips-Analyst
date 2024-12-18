🍽️ Restaurant Tips Analysis
![image](https://github.com/user-attachments/assets/d0903934-e534-4107-91e2-bb13c5237b51)

This project aims to use the restaurant tips dataset to practice creating composition plots and visualizations. We will examine the relationship between different variables and the tips given.

The dataset consists of information from 244 restaurant bills, collected in the US in 1987.

It includes details about the tips given to restaurant staff, such as the total bill, tip amount, gender of the person paying, smoking status, day of the week, time of day, and party size.
## **👣 The First Steps**

### **📥 Data import**

First, let's import the needed libraries: Pandas & Matplotlib.
import pandas as pd
import matplotlib.pyplot as plt
##FIRST
Then load data from the following link: https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv

##### df = pd.read_csv('https://raw.githubusercontent.com/RusAbk/sca_datasets/main/tips.csv')

### **🔍 Data exploration**

#### **Test sample**

Let's take a look at the first 5 rows to be sure, that data is loaded properly:

#### df.head(5)
![image](https://github.com/user-attachments/assets/cd450a1a-a95e-44fc-b45f-0fde5faf3654)

> 🎉 Great! It seems to be okay.

## As you can see each observation represents a customer who left a tip at a restaurant.

### We can see information about:
 * the day it occurred
 * if it was at lunch or dinner
 * the total bill
 * the sex of the person
 * if they were a smoker or not
 * the size of the party 

### Before continuing take a look at a few rows of the data and use `info` and `describe` to analyze dataset column types and values.

#### **Column types checking**

#### Show the columns of the dataframe and their types:

#### df.info()

![image](https://github.com/user-attachments/assets/8f1c653f-0a31-47df-a3c8-c6fa39edee0c)

> **Ooops... 🤔**
>
> We have string columns considered as objects.

<u>Let's fix their types and make them string:</u>

#### df = df.convert_dtypes()

#### Check again (output columns and their types):

df.info()
![image](https://github.com/user-attachments/assets/a8bd53de-f478-4c96-9c35-e73ab5c51fb8)


Nice! We finished this. Look like we are ready to explore some statistics on the given data.

#### **Basic descriptive statistics**

<u>Show a descriptive statistics of the numeric columns:</u>

df.describe()
![image](https://github.com/user-attachments/assets/81bcd267-7e8f-4067-aecf-f02bc3f6ecf0)

Great! Now we know a little more about our data.

➡️ Let's move forward!

## **💸 Tip value influencers**

### **🚬 Do people who smoke give more tips?**

Let's figure out the difference between smokers and non-smokers in terms of their behavior and purchasing habits in public catering establishments.

#### **Separate smokers and non-smokers**

<u>Create a new dataframe `smokers_df` containing only info about smokers.</u>

#### smokers_df = df[df['smoker'] =='Yes']

<u>Check whether everything is okay. Output a test sample (5 random rows):</u>

#### smokers_df.sample(5)
![image](https://github.com/user-attachments/assets/d688c022-e225-4d99-92e6-9cd40717b503)

<u>Also create another one dataframe `non_smokers_df` containing only non-smokers.</u>

#### non_smokers_df = df[df['smoker'] == 'No']

<u>Check whether everything is okay. Output a test sample (5 random rows):</u>

#### non_smokers_df.sample(5)
    ![image](https://github.com/user-attachments/assets/0f5b21ed-dcc7-4f1f-8d1a-fc6af6fd9bfd)

#### **Compare their measures of central tendency**

As we know, measures of central tendency is one of the basic tools, that allow us to compare different datasets as it shows the most typical values.

##### **🌏 Whole dataset**

Let's try to calculate measures of central tendency for the whole dataset first.

Calculate them for the **'tip'** column through the whole dataset and save them into the following variables:

* min => `common_tip_min`

* max => `common_tip_max`

* mean => `common_tip_mean`

* median => `common_tip_median`

common_tip_min = df.tip.min()

common_tip_max = df.tip.max()

common_tip_mean = df.tip.mean()

common_tip_median = df.tip.median()

Let's show the resulting values for whole dataset (we already have the code written for you 😉)

# Make a list of values
common_values = [common_tip_min, common_tip_max, common_tip_mean, common_tip_median]
# Round all the values to 4 decimal places
common_values = map(lambda x: round(x, 4), common_values)

# Make a dataframe from the list
common_mct = pd.DataFrame(common_values, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
common_mct

##### **🚬 Smokers**

Do the same taking into account only smokers. Use the following variables:

* min => `smokers_tip_min`

* max => `smokers_tip_max`

* mean => `smokers_tip_mean`

* median => `smokers_tip_median`

smokers_tip_min = smokers_df.tip.min()

smokers_tip_max = smokers_df.tip.max()

smokers_tip_mean = smokers_df.tip.mean()

smokers_tip_median = smokers_df.tip.median()

Let's output the results in the same format.

Make the same dataframe containing the measures of central tendency for smokers as we did for whole dataset. Then output it.

# Make a list of values
smokers_values = [smokers_tip_min, smokers_tip_max, smokers_tip_mean, smokers_tip_median]
# Round all the values to 4 decimal places
smokers_values = map(lambda x: round(x, 4), smokers_values)

# Make a dataframe from the list
smokers_mct = pd.DataFrame(smokers_values, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
smokers_mct
![image](https://github.com/user-attachments/assets/6db40203-d114-4065-95d5-f3ca623585b7)

##### **🚭 Non-smokers**

Now repeat it for non-smokers. Use the following variables:

* min => `non_smokers_tip_min`

* max => `non_smokers_tip_max`

* mean => `non_smokers_tip_mean`

* median => `non_smokers_tip_median`

non_smokers_tip_min = non_smokers_df.tip.min()

non_smokers_tip_max = non_smokers_df.tip.max()

non_smokers_tip_mean = non_smokers_df.tip.mean()

non_smokers_tip_median = non_smokers_df.tip.median()

Make the same dataframe containing the measures of central tendency for non-smokers as we did for whole dataset. Then output it.

non_smokers_values = [non_smokers_tip_min,non_smokers_tip_max,non_smokers_tip_mean,non_smokers_tip_median]

non_smokers_values = map(lambda x: round(x, 4), non_smokers_values)

# Make a dataframe from the list
non_smokers_mct = pd.DataFrame(non_smokers_values, index=['min', 'max', 'mean', 'median'])
# Output the dataframe
non_smokers_mct
![image](https://github.com/user-attachments/assets/63ddff98-febd-471a-a5dc-aa865656cb9f)

##### **📝 Conclusion**

Let's show the retrieved results together (we already have the code written for you 😉):

all_vals_dict = {
    'Common': {'min':common_tip_min, 'max': common_tip_max, 'mean': common_tip_mean, 'median': common_tip_median},
    'Smokers': {'min': smokers_tip_min, 'max': smokers_tip_max, 'mean': smokers_tip_mean, 'median': smokers_tip_median},
    'Non-smokers': {'min': non_smokers_tip_min, 'max': non_smokers_tip_max, 'mean': non_smokers_tip_mean, 'median': non_smokers_tip_median}
}

# Make a dataframe
all_mct = pd.DataFrame(all_vals_dict)
# Output the dataframe
all_mct
![image](https://github.com/user-attachments/assets/bde94516-f99e-4665-9489-1180f4b35718)


**Insights based on measures of central tendency comparison:**

---

### 1. Insight 1 the smokers tip more than Non-smokers.
### 2. Insight 2 the non-smokers tip less than the smokers.

**General conclusion:**

#### **Look at histograms**

As we already discussed on the last lecture, there are a lot of cases, when comparing the measures of central tendency is not enough.

This is because they only show the most typical values. However, the way data is distributed is equally important. There are situations where measures of central tendency are exactly the same, but due to different distributions, it is incorrect to say that the datasets are similar.

##### **🌏 Whole dataset tips histogram**

Plot the histogram for the whole dataset tips distribution.

<u>Use the following settings:</u>

* Size: `15 x 5`

* Color: `#74b9ff`

* X-axis label: `Tip value`

* Y-axis label: `Frequency`

* Chart title: `Whole dataset tip values`

* Gridlines: `show`

plt.figure(figsize=(15,3))

plt.hist(df.tip,color='#74b9ff')

plt.title("Whole dataset tip values")

plt.xlabel("Tip value")

plt.ylabel("Frequency")

plt.grid(True)

plt.legend()

![image](https://github.com/user-attachments/assets/90b1c9e8-3d24-4d9a-b3d8-1ec15f73f385)

##### **🚬 Smokers tips histogram**

#### Plot the histogram for smokers tips distribution.

<u>Use the following settings:</u>

* Size: `15 x 5`

* Color: `#ff7675`

* X-axis label: `Tip value`

* Y-axis label: `Frequency`

* Chart title: `Smokers tip values`

* Gridlines: `show`

plt.figure(figsize=(15,3))

plt.hist(smokers_df['tip'],color='#ff7675')

plt.xlabel='Tip value'

plt.ylabel= 'Frequency'

plt.title= 'Smokers tip values'

plt.grid=True

![image](https://github.com/user-attachments/assets/c88c4989-fcc9-47a2-b54d-e57eea64d2af)

##### **🚭 Non-smokers tips histogram**

Plot the histogram for non-smokers tips distribution.

<u>Use the following settings:</u>

* Size: `15 x 5`

* Color: `#55efc4`

* X-axis label: `Tip value`

* Y-axis label: `Frequency`

* Chart title: `Non-smokers tip values`

* Gridlines: `show`

plt.figure(figsize=(15,5))

plt.hist(non_smokers_df['tip'],color='#55efc4')

plt.xlabel = 'Tip value'

plt.ylabel = 'Frequency'

plt.title = 'Non-smokers tip values'

plt.grid= True

![image](https://github.com/user-attachments/assets/32a6419b-e4ff-47ab-bf3a-738cd385ed1f)

##### **⭐ Extra-task with a higher difficulty**

Plot all 3 charts in a row in the same cell:

figure, axis = plt.subplots(1,3,figsize=(20,5))

axis[0].hist(df.tip,bins=5,color='red')

axis[0].set_title("Whole dataset tip values")

axis[1].hist(smokers_df.tip,bins=5,color='blue')

axis[1].set_title("Smokers tip values")

axis[2].hist(non_smokers_df.tip,bins=5,color='green')

axis[2].set_title("non smokers tip value")

plt.show()

![image](https://github.com/user-attachments/assets/05a2796f-5043-417c-af04-1db8c0a6da48)

##### **📝 Conclusion**

**Insights based on distribution comparison:**

### Smokers is tip more than other.
---

### **👨👩 Do males give more tips?**

Perform the same steps based on the column **sex**.

male_tip_min = df[df['sex'] == 'Male'].tip.min()

male_tip_max = df[df['sex'] == 'Male'].tip.max()

male_tip_mean = df[df['sex'] == 'Male'].tip.mean()

male_tip_median = df[df['sex'] == 'Male'].tip.median()

female_tip_min = df[df['sex'] == 'Female'].tip.min()

female_tip_max = df[df['sex'] == 'Female'].tip.max()

female_tip_mean = df[df['sex'] == 'Female'].tip.mean()

female_tip_median = df[df['sex'] == 'Female'].tip.median()

all_vals_dict_mf = {
    'Male': {'min': male_tip_min, 'max': male_tip_max, 'mean': male_tip_mean, 'median': male_tip_median},
    'Female': {'min': female_tip_min, 'max': female_tip_max, 'mean': female_tip_mean, 'median': female_tip_median}
}

## Make a dataframe
all_mct = pd.DataFrame(all_vals_dict_mf)
## Output the dataframe
all_mct

df_male = df[df['sex'] == 'Male']

df_female = df[df['sex'] == 'Female']

figure, axis = plt.subplots(1,2,figsize=(20,5))

axis[0].hist(df_male['tip'],bins=5,color='red')

axis[0].set_title("male tip values")

axis[1].hist(df_female['tip'],bins=5,color='blue')

axis[1].set_title("female tip values")

plt.show()

![image](https://github.com/user-attachments/assets/3613ca32-6bfc-4557-97c9-ce4c8e8d7ac2)

### **📆 Do weekends bring more tips?**

Perform the same steps based on the column **day**.

df.head()

df_thur= df[df['day'] == 'Thur']

df_fri = df[df['day'] == 'Fri']

df_sat = df[df['day'] == 'Sat']

df_sun = df[df['day'] == 'Sun']

figure, axis = plt.subplots(1,4,figsize=(20,5))

axis[0].hist(df_thur['tip'],bins=5,color='red')

axis[0].set_title("thurday tip value")

axis[1].hist(df_fri['tip'],bins=5,color='blue')

axis[1].set_title("friday tip value")

axis[2].hist(df_sat['tip'],bins=5,color='green')

axis[2].set_title("saturday tip value")

axis[3].hist(df_sun['tip'],bins=5,color='yellow')

axis[3].set_title("sunday tip value")

plt.show()

![image](https://github.com/user-attachments/assets/2f5deee9-5e1f-48cb-b4c1-1e33f1023852)


### **🕑 Do dinners bring more tips?**

Perform the same steps based on the column **time**.

df_dinner = df[df['time'] == 'Dinner']

df_lunch = df[df['time'] == 'Lunch']

figure, axis = plt.subplots(1,2,figsize=(20,5))

axis[0].hist(df_dinner['tip'],bins=5,color='red')

axis[0].set_title("dinner tip values")

axis[1].hist(df_lunch['tip'],bins=5,color='blue')

axis[1].set_title("lunch tip values")

plt.show()

![image](https://github.com/user-attachments/assets/b675a65d-aea5-4f3f-a8a2-fa74bcf35232)
