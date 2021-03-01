# Cleaning-and-analaysing-medical-data

This Pythopn 3 script cleans data saved as a string, converts it into lists, and then analyses it.

# This script uses Python String Methods to transform and clean up medical data. It was then analysed.

medical_data = \
"""Marina Allison   ,27   ,   31.1 , 
#7010.0   ;Markus Valdez   ,   30, 
22.4,   #4050.0 ;Connie Ballard ,43 
,   25.3 , #12060.0 ;Darnell Weber   
,   35   , 20.6   , #7500.0;
Sylvie Charles   ,22, 22.1 
,#3022.0   ;   Vinay Padilla,24,   
26.9 ,#4620.0 ;Meredith Santiago, 51   , 
29.3 ,#16330.0;   Andre Mccarty, 
19,22.7 , #2900.0 ; 
Lorena Hodson ,65, 33.1 , #19370.0; 
Isaac Vu ,34, 24.8,   #7045.0"""

# Looking at what is contained in the string
print(medical_data)

# Representing the insurance cost in dollars: beginning the data cleaning
updated_medical_data = medical_data.replace("#", "$")
print(updated_medical_data)

# Calculating the number of medical records in our data
num_records = 0
for record in updated_medical_data:
  if record == "$":
     num_records += 1
counted_number_of_records = "There are {} medical records in the data."
print(counted_number_of_records.format(num_records))

# Cleaning up the data: splitting the string into a list of each medical record
medical_data_split = updated_medical_data.split(";")
print(medical_data_split)

# Splitting each medical record into its own list, for readability
medical_records = []
for record in medical_data_split:
  medical_records.append(record.split(","))
print(medical_records)

# Removing the whitespace
medical_records_clean = []
# outside loop that goes through each record in medical_records
for record in medical_records:
  # empty list that will store each cleaned record
  record_clean = []
  # nested loop to go through each item in each medical record
  for item in record:
    # cleaning the whitespace for each record using item.strip()
    record_clean.append(item.strip())
  # add the cleaned medical record to the medical_records_clean list
  medical_records_clean.append(record_clean)
  print(medical_records_clean)

# The data is now ready for analysis. Analysing the contents:
for record in medical_records_clean:
  record[0] = record[0].upper()
  print(record[0])

# Separating useful lists:
names = []
ages = []
bmis = []
insurance_costs = []
for record in medical_records_clean:
  # append the name, age, BMI, and insurance cost from the current medical record 
  names.append(record[0])
  ages.append(record[1])
  bmis.append(record[2])
  insurance_costs.append(record[3])
print("Names: " + str(names))
print("Ages: " + str(ages))
print("BMI: "  + str(bmis))
print("Insurance Costs: " + str(insurance_costs))

# Analysis: calculating the average BMI in the dataset
total_bmi = 0
for value in bmis:
  total_bmi += float(value)
average_bmi = total_bmi/len(bmis)
print("Average BMI: " + str(average_bmi))



