# PyCitySchools with Pandas - FRM's Tec Data Bootcamp Challenge #4

## Overview of the school district analysis

### Purpose
After a thorough data analysis work with the district and charter schools of the district we labor in, we have been notified that ninth grades of Thomas High School may have commited infringement regarding academic honesty, for which the school board has requested our boss Maria and I to run the analysis on the district schools once again, turning null the math and reading scores obtained by nine-graders of the mentioned school and visually showing how this change affects the whole analysis ran for all the district and charter school in the district.


## Results

### How is the district summary affected?
- Original result
![image](https://user-images.githubusercontent.com/96660344/151742152-53101ff2-2328-448f-b743-7bb21b368dc5.png)

- Modified result
![image](https://user-images.githubusercontent.com/96660344/151740226-0496026c-bba5-42ac-8174-c2cab6809832.png)

461 students are not counted in the modified result, and changes vary from -0.1% to -0.3%.

### How is the school summary affected?
- Original result
![image](https://user-images.githubusercontent.com/96660344/151742203-a878f833-410c-4ee9-aeb9-938ca7fe2500.png)


- Modified result
![image](https://user-images.githubusercontent.com/96660344/151743000-62f4a3b9-0d70-4f2e-8fba-b38231cea085.png)

There's a slight change of 0.317688% after not counting the 461 students accordingly. 

### How does replacing the ninth graders' math and reading scores affect Thomas High School's performance relative to the other schools?
- Original result
![image](https://user-images.githubusercontent.com/96660344/151742076-c048939e-af89-45cd-9179-bd0c7ea0d1a0.png)


- Modified result
![image](https://user-images.githubusercontent.com/96660344/151741272-5b04951c-828f-4760-bd49-99cdf5e84919.png)

Making reference to the previous change of 0.317688%, Thomas High School still remains as the second best performer school of the distrcit, wtih a 0.030869% advantage over Griffin High School.

### How does replacing the ninth-grade scores affect the following:
- Math scores by grade
  - Original result
 
    ![image](https://user-images.githubusercontent.com/96660344/151741798-7d600a9a-a7f7-4689-b640-f2f95055747d.png)

  - Modified result 

    ![image](https://user-images.githubusercontent.com/96660344/151741878-b8ef2cf9-1f16-4ef6-afd9-83890b5a35a5.png)
  
  We change the format to a nan (not a number) to avoid wrong calculations that would take place if we instead replaced the 9th grade scores with a "0".


- Reading scores by grade
  - Original result
  
    ![image](https://user-images.githubusercontent.com/96660344/151741777-7017ee50-dc6e-46b1-98a2-5ca6d651a7eb.png)

  - Modified result
 
    ![image](https://user-images.githubusercontent.com/96660344/151741857-d30e29f5-903c-439f-a36e-c994f849f4a2.png)

   We performed the same process as with the math scores, with a "nan" as result.


- Scores by school spending
  - Original result
  ![image](https://user-images.githubusercontent.com/96660344/151740806-a7d1c206-e844-4c23-85e9-852299b7a2ba.png)

  
  - Modified result
![image](https://user-images.githubusercontent.com/96660344/151741051-01a26678-ecbb-4e06-93fe-5b48e3de32f2.png)

  No major changes occur.
 
- Scores by school size
  - Original result

    ![image](https://user-images.githubusercontent.com/96660344/151740654-35e35f81-6171-4e1a-bb09-c4eb7d0fdcb7.png)


  - Modified result  
  ![image](https://user-images.githubusercontent.com/96660344/151739839-809ea634-246e-492c-9264-dbf012f55acb.png)

  No major changes occur.

-  Scores by school type
    - Original result

      ![image](https://user-images.githubusercontent.com/96660344/151740558-a9fafa1d-da7f-4341-89be-281e68fe0083.png)

    - Modified result 

      ![image](https://user-images.githubusercontent.com/96660344/151739703-63605e6d-bdb5-4dda-99f8-bdb5f1c93697.png)

    No major changes occur.

## Summary

### Change 1 - Output
The first visible change relies on the fact of integers in 9th grade scores going to "nan" after we replace their values to not take them into consideration.

### Change 2 - Tricky Data
If we do not complete step #5 we see a 25.871559% change in overall passing for THS which results illogic taking into consideration that we are taking out of the calculus 9th grade, meaning that the overral passing percentage would be determined by the 3 remaining grades (10th, 11th and 12th). If we replaced the nan for a 0 this 25.871559% would make sense, but this is not the case and if we don't take this into consideration the school board may take serious actions against THS when not really necessary.

![image](https://user-images.githubusercontent.com/96660344/151745609-ee38c32f-871d-4baa-9bab-c9e436fcc681.png)

In step #5, we add the following and the data is corrected as displayed previously in this report under question "How is the school summary affectd?":

students_ths_rest = school_data_complete_df.loc[(
    (school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["grade"] != "9th")), "Student ID"].count()

### Change 3 - Scores
Neither for spending, size nor type we see major changes despite the changes performed for the 9th graders of THS. Thus, we can infer that such little population have little impact in the analysis, as it only represents 0.0117692111309676% (1.1%) of the total enrollment of the district. 

Other story would be if all THS grades were not taken into consideration, which would represent 0.041741128414603% (4.17%) of the total enrollment of the district.

### Change 4 - District Summary
Even as it is only visual, the total amount of students taken into consideration decreases with the modification of 9th graders by 461 students in total.

