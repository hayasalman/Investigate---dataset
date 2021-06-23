# Investigate---dataset
 analyze a dataset by ython libraries NumPy, pandas, and Matplotlib 
#import pandas, numpy and matplotlib.
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
% matplotlib inline
#load CSV file
df = pd.read_csv('medical_appointment.csv')
df.head()
df.shape
#assessing and cleaning dataset
df.info()
df.nunique()
df.dtypes
df.drop(['AppointmentID', 'ScheduledDay', 'AppointmentDay', 'Neighbourhood', 'Scholarship'], axis=1, inplace=True)
df.head(10)
sum(df.duplicated())
df.drop_duplicates(inplace=True)
sum(df.duplicated())#check again
#we want to see if the reminder messages has something to do with the no show.
df.groupby('No-show').SMS_received.count()
df.groupby('SMS_received').count()
df.groupby('No-show').SMS_received.count().plot(kind='bar')
plt.title('Patients received reminder masseges Vs.Patients show up on appointment')
plt.xlabel('Show up on appointment')
plt.ylabel('Patient received SMS');
#Average of the patient age
df.groupby('Gender').mean().Age.plot(kind='bar')
plt.title('Average age of the male/female patients')
plt.xlabel('gender')
plt.ylabel('age in numbers')
df.groupby('Gender').mean().Age
df.describe().Age
#the Gender of the patient
df.groupby('Gender').count().PatientId
#Hipertension Vs. Diabetes
df.Hipertension.hist(alpha=0.5, label='Hipertension')
df.Diabetes.hist(alpha=0.5, label='Diabetes')
plt.title('Hipertension Vs. Diabetes')
plt.xlabel('diseases')
plt.ylabel('number of patient')
plt.legend()
df.groupby('Hipertension').Gender.count()
df.groupby('Diabetes').Gender.count()
#Alcoholism Vs. Handcap 
df.Alcoholism.hist(alpha=0.5, label='Alcoholism')
df.Handcap.hist(alpha=0.5, label='Handcap')
plt.title('Alcoholism Vs. Handcap')
plt.xlabel('diseases')
plt.ylabel('number of patient')
plt.legend()
df.groupby('Alcoholism').Gender.count()
df.groupby('Handcap').Gender.count()
df.to_csv('medical_appointment.csv', index=False)
