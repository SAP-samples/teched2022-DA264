# Hands-on - Part 2 (Govern and Monitor Data Quality)

In this exercise, you will continue to interact with the enriched dataset you created in the previous part.
You will first modify the recipe you used to create that dataset, schedule a publication so it can take into account potential metadata changes in the future.
Then you will create rules and a rulebook to visually track the data quality issues that were found.
Finally you will curate the data.

## Modify Preparation

After completing these steps you will have modified your data preparation recipe to further isolate the data quality issues on a specific column.
Then you will schedule a publication of this dataset to take into account potantial metadata changes in the future.

1. Click 'View Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part01_01.png)

2. Click 'DRUG_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_02.png)

3. This opens your preparation.
<br>![](/exercises/ex2/images/Ex02_Part01_03.png)

4. Click 'Recipe'.
<br>![](/exercises/ex2/images/Ex02_Part01_04.png)

5. Edit the 'Enrich' action.
<br>![](/exercises/ex2/images/Ex02_Part01_05.png)

6. This opens the Enrich window with the defined Enrich action.
<br>![](/exercises/ex2/images/Ex02_Part01_06.png)

7. Click the 'Join' icon.
<br>![](/exercises/ex2/images/Ex02_Part01_07.png)

8. The join definition window opens. Scroll down to the bottom of Output Columns.
<br>![](/exercises/ex2/images/Ex02_Part01_08.png)

9. Check 'POTENCY', under Right Source.
<br>![](/exercises/ex2/images/Ex02_Part01_09.png)

10. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part01_10.png)

11. 'POTENCY' is now added in the output columns.
<br>![](/exercises/ex2/images/Ex02_Part01_11.png)

12. Click 'Apply Enrichment'.
<br>![](/exercises/ex2/images/Ex02_Part01_12.png)

13. The daset is now enriched with the additional selected column.
<br>![](/exercises/ex2/images/Ex02_Part01_13.png)

14. Click 'Recipe'.
<br>![](/exercises/ex2/images/Ex02_Part01_14.png)

15. Edit the 'Add Column ValidClaim' action.
<br>![](/exercises/ex2/images/Ex02_Part01_15.png)

16. Change the 'Column Name' from ValidClaim to VALID_DRUG.
<br>![](/exercises/ex2/images/Ex02_Part01_16.png)

17. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part01_17.png)

18. The column name has changed.
<br>![](/exercises/ex2/images/Ex02_Part01_18.png)

19. Click 'Add Filter'.
<br>![](/exercises/ex2/images/Ex02_Part01_19.png)

20. Select 'VALID_DRUG'.
<br>![](/exercises/ex2/images/Ex02_Part01_20.png)

21. Type 'NO' in the associated filter text field.
<br>![](/exercises/ex2/images/Ex02_Part01_21.png)

22. Press Enter key to validate the filter.
<br>![](/exercises/ex2/images/Ex02_Part01_22.png)

23. This filters the data with only claims containing an invalid drug.
<br>![](/exercises/ex2/images/Ex02_Part01_23.png)

24. Click the menu icon next to the 'DRUG_NAME' column header..
<br>![](/exercises/ex2/images/Ex02_Part01_24.png)

25. Click the sort ascending icon.
<br>![](/exercises/ex2/images/Ex02_Part01_24_new.png)

26. The data are sorted by 'DRUG_NAME' by ascending order, but the first records contains null values.
<br>![](/exercises/ex2/images/Ex02_Part01_25.png)

27. Click 'Add Filter'.
<br>![](/exercises/ex2/images/Ex02_Part01_26.png)

28. Select 'DRUG_NAME'.
<br>![](/exercises/ex2/images/Ex02_Part01_26_new.png)

29. Click the '=' icon associated to the 'DRUG_NAME' filter.
<br>![](/exercises/ex2/images/Ex02_Part01_27.png)

30. Select 'Not Null'.
<br>![](/exercises/ex2/images/Ex02_Part01_28.png)

31. This shows only the claims with unknown drugs which are not null.
<br>![](/exercises/ex2/images/Ex02_Part01_29.png)

32. Click '<' to come back to the Actions menu.
<br>![](/exercises/ex2/images/Ex02_Part01_30.png)

33. Click 'Aggregate Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part01_31.png)

34. The filter defined in the main (previous screen) data preparation are automatically pre-defined in the aggregation window.
<br>![](/exercises/ex2/images/Ex02_Part01_32.png)

35. Drag and drop 'DRUG_NAME' to 'Output Columns'.
<br>![](/exercises/ex2/images/Ex02_Part01_33.png)

36. This defines the aggregation with a preview of the result at the bottom half of the screen.
<br>![](/exercises/ex2/images/Ex02_Part01_34.png)

37. Drag and drop 'DRUG_NAME' in the 'Output Columns' area.
<br>![](/exercises/ex2/images/Ex02_Part01_35.png)

38. This will generate an expected error message as right now the system considers we are trying to aggregate data twice on the same column.
<br>![](/exercises/ex2/images/Ex02_Part01_36.png)

39. Change the Aggregation function from 'No Aggregation' to 'Count'.
<br>![](/exercises/ex2/images/Ex02_Part01_37.png)

40. This shows the preview of the aggregation that contains the distinct values of drug names with their respective count.
<br>![](/exercises/ex2/images/Ex02_Part01_38.png)

41. Click 'Apply Aggregation'.
<br>![](/exercises/ex2/images/Ex02_Part01_39.png)

42. The main data preparation room now contains the aggregated data. The data could be exported as-is (as this is based only on a sample of the data) for further study and analysis. We can see already some simple data quality issues in the name of the drugs which we will curate later on.
<br>![](/exercises/ex2/images/Ex02_Part01_40.png)

43. For now, we can disable this aggregation (but still keep it's definition). Click 'Recipe'.
<br>![](/exercises/ex2/images/Ex02_Part01_42.png)

44. Click 'More Actions' ('...') for the 'Aggregate' action in the recipe.
<br>![](/exercises/ex2/images/Ex02_Part01_43.png)

45. Click 'Disable'.
<br>![](/exercises/ex2/images/Ex02_Part01_44.png)

46. The aggregation action is now disabled. The data preparation room shows the data prior executing the aggregation. The filters that were defined were automatically removed (but are still embedded in the definition of the aggregation). At any point of time, we can come back to this data preparation recipe and reactivate this action.
<br>![](/exercises/ex2/images/Ex02_Part01_45.png)

47. Click 'Actions'.
<br>![](/exercises/ex2/images/Ex02_Part01_46.png)

48. Click 'Run Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part01_47.png)

49. Click the 'Container' icon.
<br>![](/exercises/ex2/images/Ex02_Part01_48.png)

50. Select 'PHARMA-CLAIMS_ENRICHED_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_49.png)

51. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part01_50.png)

52. Note: with 'Write Mode' set to 'Overwrite' will allow the content to overwrite the existing data with this new definition.
<br>![](/exercises/ex2/images/Ex02_Part01_51_new.png)

53. Click 'Apply'.
<br>![](/exercises/ex2/images/Apply.png)

54. Click 'Yes'.
<br>![](/exercises/ex2/images/Ex02_Part01_52.png)

55. Wait until you see a notification for the task being completed. You can click on the refresh button on the bottom of the screen.
<br>![](/exercises/ex2/images/Ex02_Part01_54_new.png)

56. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

57. Click 'Browse Connections'.
<br>![](/exercises/ex2/images/Ex02_Part01_54.png)

58. Click 'DI_DATA_LAKE'.
<br>![](/exercises/ex2/images/Ex02_Part01_55.png)

59. Click 'shared'.
<br>![](/exercises/ex2/images/Ex02_Part01_56.png)

60. Filter the data with '*_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_57.png)

61. Click 'TechEd_DA264_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_58.png)

62. Click 'View Fact Sheet' for the file 'PHARMA_CLAIMS_ENRICH_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_59.png)

63. The application shows the Fact Sheet associated to the selected dataset.
<br>![](/exercises/ex2/images/Ex02_Part01_60.png)

64. Click 'Columns'.
<br>![](/exercises/ex2/images/Ex02_Part01_61.png)

65. The columns are not profiled anymore. This is because the structure of the data changed when we modified the definition in the recipe associated to the preparation task (added the column POTENCY, changed one column name).
<br>![](/exercises/ex2/images/Ex02_Part01_62.png)

66. Click 'Profile Data'.
<br>![](/exercises/ex2/images/Ex02_Part01_63.png)

67. Click 'Yes'.
<br>![](/exercises/ex2/images/Ex02_Part01_64.png)

68. Click 'Refresh'.
<br>![](/exercises/ex2/images/Ex02_Part01_66.png)

69. Wait to see 'Profiled:' time stamp has changed indicating that the profile task finished successfully.
<br>![](/exercises/ex2/images/Ex02_Part01_65.png)

70. The data is now profiled again, there is a new version of the profiling information available. Click 'Columns'. Note: Previous information of the profiling metadata stays available.
<br>![](/exercises/ex2/images/Ex02_Part01_67.png)

71. All the new profiling information are available.
<br>![](/exercises/ex2/images/Ex02_Part01_68.png)

72 Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

73. Click 'Home'.
<br>![](/exercises/ex2/images/ClickHome.png)

Because you changed the structure of the dataset, you will also need to publish the dataset once again to the catalog.
However, instead of repeating this operation, you can schedule the publication of the dataset instead of doing it manually every time the structure of the data changes.

74. Click 'scheduled tasks' to create a new scheduled task.
<br>![](/exercises/ex2/images/Ex02_Part01_70.png)

75. Click 'Add' to add a new task.
<br>![](/exercises/ex2/images/Ex02_Part01_71.png)

76. Click the 'Name' field to select the publication name to schedule.
<br>![](/exercises/ex2/images/Ex02_Part01_72.png)

77. Type 'pharma claims publication ##' in the 'Filter Publications' text field. (Where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part01_73.png)

78. Select your publication (for example if you are user 99, select Pharma Claims Publication 99).
<br>![](/exercises/ex2/images/Ex02_Part01_74.png)

79. Click 'OK'.
<br>![](/exercises/ex2/images/Ex02_Part01_75.png)

80. Open the 'Picker' icon for the Start Time to give you few more minutes for the first schedule of the selected publication.
<br>![](/exercises/ex2/images/Ex02_Part01_76.png)

81. Click on the minutes and add 5 more minutes to the original value. For example, if the value was 06:45, set it to 06:50. Click 'OK'.
<br>![](/exercises/ex2/images/Ex02_Part01_77.png)

82. Click 'OK'.
<br>![](/exercises/ex2/images/Ex02_Part01_78_new.png)

83. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part01_78.png)

84. Wait until the scheduled publication task is executed.
<br>![](/exercises/ex2/images/Ex02_Part01_79.png)

85. Click the Refresh icon or check notifications to see when the scheduled publishing task is complete.
<br>![](/exercises/ex2/images/Ex02_Part01_82_1new.png)
<br>![](/exercises/ex2/images/Ex02_Part01_82_new.png)

86. Once done, the status will change to 'Completed'.
<br>![](/exercises/ex2/images/Ex02_Part01_80.png)

87. Click on the scheduled task to see the details.
<br>![](/exercises/ex2/images/Ex02_Part01_81.png)

88. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

88. Click 'Home'.
<br>![](/exercises/ex2/images/ClickHome.png)

89. You are back to the Metadata Explorer home page.
<br>![](/exercises/ex2/images/Ex02_Part01_83.png)

You have now modified your data preparation recipe to further isolate the data quality issues on a specific column.
You also have scheduled a publication of this dataset to take into account potantial metadata changes in the future.

## Business Glossary

After completing these steps you will have created a glossary and business terms and associated them to your enriched dataset.

1. Click 'glossaries' to access or create a new glossary.
<br>![](/exercises/ex2/images/Ex02_Part02_01.png)

2. You can access or create glossaries.
<br>![](/exercises/ex2/images/Ex02_Part02_02.png)

3. Click '+'.
<br>![](/exercises/ex2/images/Ex02_Part02_03.png)

4. Type 'DRUGS_GLOSSARY_##' in the 'Name' text field (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part02_04.png)

5. Select 'Glossary' from the Template drop down menu.
<br>![](/exercises/ex2/images/Ex02_Part02_05.png)

6. Type the following description: 'Glossary for pharmaceutical drugs'.
<br>![](/exercises/ex2/images/Ex02_Part02_06.png)

7. Click 'Save' to create the glossary.
<br>![](/exercises/ex2/images/Ex02_Part02_08.png)

8. You created a glossary, and now can start enriching it with new terms.
<br>![](/exercises/ex2/images/Ex02_Part02_09.png)

9. Click 'Edit Term Template'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_01.png)

10. Click 'Custom Attribute'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_02.png)

11. Click 'Add Custom Attribute Group'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_03.png)

12. Type 'Pharma Drug Attributes' for 'Enter Group Name'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_04.png)

13. Click 'Add Attribute'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_05.png)

14. Type 'Form' for Name.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_06.png)

15. Type 'Pharmaceutical form of medicinal products' for Description.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_07.png)

16. Type 'String' from the Type drop down list.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_08.png)

17. Type 'List of Values' from the Validation Type drop down list.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_09.png)

18. Type 'Liquid' and the Enter key for Valid Values.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_10.png)

19. Type 'Tablet' <press the Enter key>, 'Capsules' <press the Enter key>. and 'Inhalers' <press the Enter key> adding to the list of Valid Values.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_11.png)

20. Click 'Ok'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_12.png)

21. Click 'Add Attribute'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_13.png)

22. Type 'Last Reviewed' for Name.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_14.png)

23. Type 'Date last reviewed' for Description.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_15.png)

24. Type 'Date' from the Type drop down list.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_16.png)

25. Click 'Ok'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_17.png)

26. Click 'Add Attribute'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_18.png)

27. Select 'Right' from Display Column drop down menu.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_19.png)

28. Type 'Reviewer' for Name.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_20.png)

29. Type 'Reviewer's name' for Description.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_21.png)

30. Type 'String' from the Type drop down list.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_22.png)

31. Click 'Ok'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_23.png)

32. Click 'Last Reviewed'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_24.png)

33. Click '>', to move 'Last Reviewed' to the right column and under 'Reviewer'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_25.png)

34. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_26.png)

35. Click '+' to create a new term.
<br>![](/exercises/ex2/images/Ex02_Part02_10.png)

36. The term creation windows shows up.
<br>![](/exercises/ex2/images/Ex02_Part02_11.png)

37. Type 'Potency' in the 'Term Name' text field.
<br>![](/exercises/ex2/images/Ex02_Part02_12.png)

38. Type the following definition for the term: 'Measure of drug activity expressed in terms of the amount required to produce an effect of given intensity'.
<br>![](/exercises/ex2/images/Ex02_Part02_13.png)

39. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part02_14.png)

40. Click the 'Go back to term list' icon.
<br>![](/exercises/ex2/images/Ex02_Part02_15.png)

41. The term 'Potency' is created and part of the glossary definitions. Click 'Potency'.
<br>![](/exercises/ex2/images/Ex02_Part02_16.png)

42. The term window shows up.
<br>![](/exercises/ex2/images/Ex02_Part02_17.png)

43. Click 'Edit'.
<br>![](/exercises/ex2/images/Ex02_Part02_18.png)

44. Click 'Pharma Drug Attribute'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_27.png)

45. Type 'Gina Milo' for Reviewer.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_28.png)
 
46. Click the Open Picker for the Last Reviewed Date.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_29.png)
 
47. Click on today's date.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_30.png)
 
48. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_31.png) 
 
49. Click 'Edit'.
<br>![](/exercises/ex2/images/Ex02_Part02_18.png)
 
50. Click 'Relationships'.
<br>![](/exercises/ex2/images/Ex02_Part02_19.png)

51. Click 'Manage Relationships'.
<br>![](/exercises/ex2/images/Ex02_Part02_20.png)

52. Click 'Datasets or Columns'.
<br>![](/exercises/ex2/images/Ex02_Part02_21.png)

53. Click 'DI_DATA_LAKE'.
<br>![](/exercises/ex2/images/Ex02_Part02_22.png)

54. Click 'shared'.
<br>![](/exercises/ex2/images/Ex02_Part02_23.png)

55. Search '*_##' (where ## is your user number) and press <Enter>.
<br>![](/exercises/ex2/images/Ex02_Part02_24.png)

56. Check your PHARMA_CLAIMS_ENRICHED_## dataset (where ## is your user number). 
<br>![](/exercises/ex2/images/Ex02_Part02_25.png)

57. You can hover over 'PHARMA_CLAIMS_ENRICHED...' to see the full name.
<br>![](/exercises/ex2/images/Ex02_Part02_25_new.png)

58.  Click 'View Columns'.
<br>![](/exercises/ex2/images/Ex02_Part02_26.png)

59. Check 'Potency'.
<br>![](/exercises/ex2/images/Ex02_Part02_27.png)

60. Click 'Save Related Objects'.
<br>![](/exercises/ex2/images/Ex02_Part02_28_new.png)

61. The term is now associated to a dataset and a column in the dataset.
<br>![](/exercises/ex2/images/Ex02_Part02_28.png)

62. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/Ex02_Part02_29.png)

63. Click 'Home'.
<br>![](/exercises/ex2/images/Ex02_Part02_31_new.png)

64. Type 'claims' in the search bar and press the <Enter> key.
<br>![](/exercises/ex2/images/Ex02_Part02_30.png)

65. The Catalog shows the results of the dataset that matches the search pattern.
<br>![](/exercises/ex2/images/Ex02_Part02_32.png)

66. Click the 'Filter' icon.
<br>![](/exercises/ex2/images/Ex02_Part02_33.png)

67. Change the Search string to 'claims*##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part02_34.png)

68. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part02_35.png)

69. Click 'More Actions'.
<br>![](/exercises/ex2/images/Ex02_Part02_36.png)

70. Click 'View Factsheet'.
<br>![](/exercises/ex2/images/Ex02_Part02_37.png)

71. Click 'Overview'.
<br>![](/exercises/ex2/images/Ex02_Part02_38.png)
 
72. Click 'Relationships'.
<br>![](/exercises/ex2/images/Ex02_Part02_39.png)

73. Click 'Dataset Terms and Tags'.
<br>![](/exercises/ex2/images/Ex02_Part02_40.png)

74. The glossary term 'Potency' is associated to the dataset.
<br>![](/exercises/ex2/images/Ex02_Part02_41.png)

75. Click 'Columns'.
<br>![](/exercises/ex2/images/Ex02_Part02_43_new.png)

76. Click 'POTENCY'.
<br>![](/exercises/ex2/images/Ex02_Part02_42.png)

77. The glossary term 'Potency' is associated to the 'POTENCY' column of the dataset.
<br>![](/exercises/ex2/images/Ex02_Part02_43.png)

You have been informed the 'Gina Milo' has changed her last name so you need to change all the values of 'Gina Milo' to 'Gina Johnson'.
 
78. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

79. Click 'Glossary'.
<br>![](/exercises/ex2/images/Ex02_Part02_44_new1.png)
 
80. Click 'View Business Glossary'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new1.png)
 
81. Click 'DRUGS_GLOSSARY_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new2.png) 

82. Click 'Edit Term Template'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new3.png) 
 
83. Click 'Custom Attributes'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new4.png) 
 
84. Click 'Edit' (pencil) icon to the right of Reviewer.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new5.png) 
 
85. Click 'View' to the right of 'Gina Milo'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new6.png) 
 
86. Click 'Edit' (pencil) icon for 'Gina Milo'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new7.png) 
 
87. For 'Replace With:' type 'Gina Johnson'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new8.png) 
  
88. Click 'Replace'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new9.png) 

89. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new10.png) 
 
90. Click '<' to go back to the term list.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new11.png) 
 
91. Click 'Potency'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new12.png)
 
92. Click 'Pharma Drug Attributes'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new13.png) 

93. Notice the Reviewer's Name has been changed to 'Gina Johnson'.
<br>![](/exercises/ex2/images/Ex02_Part02_Attribute_44_new14.png) 
 
94. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/Ex02_Part02_44.png)

95. Click 'Home'.
<br>![](/exercises/ex2/images/Ex02_Part02_44_ner.png)

96. You are back to the Data Intellience Metadata Explorer Home page.
<br>![](/exercises/ex2/images/Ex02_Part02_45.png)

You have now created a glossary, custom attributes, which extend the meaning of an asset beyond the definition, [erformed a mass update on a custom attribute value, defined a business term, and associated the business term to a dataset and a column all to enriched your dataset.

## Rules

After completing these steps you will have created rules and a rulebook that is evaluating the data quality of your enriched dataset.

1. Click 'rules' to access existing or create new rules.
<br>![](/exercises/ex2/images/Ex02_Part03_01.png)

2. Click 'Creat Rule' to create a new 'Completeness' rule.
<br>![](/exercises/ex2/images/Ex02_Part03_02.png)

3. Select 'Completeness' from the Category drop down.
<br>![](/exercises/ex2/images/Ex02_Part03_03_new.png)

4. Type 'DRUG_NAME_EXISTS_##' for 'Rule ID' (where ## is your user id).
<br>![](/exercises/ex2/images/Ex02_Part03_04_new.png)

5. Type 'DRUG_NAME_EXISTS_##' for 'Name' (where ## is your user id).
<br>![](/exercises/ex2/images/Ex02_Part03_05_new.png)
 
6. Type the following 'Drug Name must not be null' for 'Description'.
<br>![](/exercises/ex2/images/Ex02_Part03_06_new.png)

7. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_05.png)

8. The rule editor window appears.
<br>![](/exercises/ex2/images/Ex02_Part03_06.png)

9. Click '+'.
<br>![](/exercises/ex2/images/Ex02_Part03_07.png)

10. Type 'DRUG_NAME' for the 'Name' of the parameter for the rule.
<br>![](/exercises/ex2/images/Ex02_Part03_08.png)

11. From the 'Type' drop down options, select 'String'.
<br>![](/exercises/ex2/images/Ex02_Part03_09.png)

12. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_11.png)

13. The parameter is created.
<br>![](/exercises/ex2/images/Ex02_Part03_12.png)

14. Click '+' to define the condition.
<br>![](/exercises/ex2/images/Ex02_Part03_13.png)

15. Type 'DRUG_NAME_NOT_NULL' for the 'Condition Name'.
<br>![](/exercises/ex2/images/Ex02_Part03_14.png)

16. Select 'DRUG_NAME' for the 'Parameter Name' drop down list.
<br>![](/exercises/ex2/images/Ex02_Part03_15.png)

17. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_16.png)

18. Click '<' to go back to the list of categories.
<br>![](/exercises/ex2/images/Ex02_Part03_17.png)

19. Click 'Create Rule'.
<br>![](/exercises/ex2/images/Ex02_Part03_19.png)

20. Type 'DRUG_NAME_VALID_##' for 'Rule ID' (where ## is your user id).
<br>![](/exercises/ex2/images/Ex02_Part03_20_new.png)

21. Type 'DRUG_NAME_VALID_##' for 'Name' (where ## is your user id).
<br>![](/exercises/ex2/images/Ex02_Part03_20_new_2.png)
 
22. Type 'The drug name is valid' for 'Description'.
<br>![](/exercises/ex2/images/Ex02_Part03_21.png)

23. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_22.png)

24. Click '+'.
<br>![](/exercises/ex2/images/Ex02_Part03_23.png)

25. Type 'DRUG_NAME_VALID' for the parameter 'Name'.
<br>![](/exercises/ex2/images/Ex02_Part03_24.png)

26. Click the 'Save' icon.
<br>![](/exercises/ex2/images/Ex02_Part03_25.png)

27. Click '+' on the 'Conditions'.
<br>![](/exercises/ex2/images/Ex02_Part03_26.png)

28. Type 'DRUG_NAME_VALID' for the 'Condition Name'.
<br>![](/exercises/ex2/images/Ex02_Part03_27.png)

29.Select 'DRUG_NAME_VALID' for the 'Parameter Name'
<br>![](/exercises/ex2/images/Ex02_Part03_27_new_2.png)

30. Select 'equals' from the 'Operator' drop down options.
<br>![](/exercises/ex2/images/Ex02_Part03_27_new_3.png)

31. Type 'YES' for the 'Value or Format'.
<br>![](/exercises/ex2/images/Ex02_Part03_27_new_4.png)

32. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_28.png)

33. Click '<' to navigate back to the list of rule categories.
<br>![](/exercises/ex2/images/Ex02_Part03_29.png)

34. You have created two different rules, now you can create a rulebook and associate these rules with a dataset.
<br>![](/exercises/ex2/images/Ex02_Part03_30.png)

35. Click 'Data Intelligence Metadata Explorer'.
<br>![](/exercises/ex2/images/ClickDI.png)

36. Click 'Rules'. 
<br>![](/exercises/ex2/images/Ex02_Part03_32.png)

37. Click 'View Rulebooks'.
<br>![](/exercises/ex2/images/Ex02_Part03_32_new.png)

38. The Rulebooks Overview window is displayed.
<br>![](/exercises/ex2/images/Ex02_Part03_33.png)

39. Click '+' to create a new rulebook.
<br>![](/exercises/ex2/images/Ex02_Part03_34.png)

40. Type 'PHARMA_CLAIMS_##' for the rulebook 'Name' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part03_35.png)

41. Type 'Set of rules to evaluate the quality of dataset used to track pharma claims' for the 'Description'.
<br>![](/exercises/ex2/images/Ex02_Part03_36.png)

42. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_37.png)

43. The empty rulebook is created.
<br>![](/exercises/ex2/images/Ex02_Part03_38.png)

44. Click 'Add Rule'.
<br>![](/exercises/ex2/images/Ex02_Part03_39.png)

45. Expand 'Accuracy'.
<br>![](/exercises/ex2/images/Ex02_Part03_40.png)

46. Check your rule named 'DRUG_NAME_VALID_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part03_41.png)

47. Collapse 'Accuracy'.
<br>![](/exercises/ex2/images/Ex02_Part03_42.png)

48. Expand 'Completeness'.
<br>![](/exercises/ex2/images/Ex02_Part03_43.png)

49. Check your rule named 'DRUG_NAME_EXISTS_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part03_44.png)

50. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part03_45.png)

51. The rules are now imported, you need to associate them with a dataset to be run against.
<br>![](/exercises/ex2/images/Ex02_Part03_46.png)
 
52. Click 'Create Rule Binding' to bind the rule with a dataset.
<br>![](/exercises/ex2/images/Ex02_Part03_47.png)

53. Click 'Step 2'.
<br>![](/exercises/ex2/images/Ex02_Part03_48.png)

54. Select 'DI_DATA_LAKE', from the 'Connections' drop down list.
<br>![](/exercises/ex2/images/Ex02_Part03_50.png)

55 Click 'shared'.
<br>![](/exercises/ex2/images/Ex02_Part03_52.png)

56 Type '*##' in the 'Filter items' parameter (where ## is your user number). 
<br>![](/exercises/ex2/images/Ex02_Part03_53.png)

57 Click your 'TechEd_DA264_##' (where ## is your user number). 
<br>![](/exercises/ex2/images/Ex02_Part03_53_new.png)

58 Type '*##' in the 'Filter items' parameter (where ## is your user number). 
<br>![](/exercises/ex2/images/Ex02_Part03_53_new_2.png)

59. Select 'PHARMA_CLAIMS_ENRICHED_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part03_54.png)

60. The dataset is selected. Click 'Step 3'.
<br>![](/exercises/ex2/images/Ex02_Part03_56.png)

61. Select 'VALID_DRUG' from the 'Mapped to Column' drop down list,
<br>![](/exercises/ex2/images/Ex02_Part03_58.png)

62. Click 'Create Binding'.
<br>![](/exercises/ex2/images/Ex02_Part03_59.png)

63. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part03_60.png)

64. Expand Accuracy.
<br>![](/exercises/ex2/images/Ex02_Part03_61_new.png)

65. Notice that you have now bound the Rule DRUG_NAME_## to the PHARMA_CLAIMS_ENRICHED_99.csv (where ## is your user number). 
<br>![](/exercises/ex2/images/Ex02_Part03_61_new_2.png)

66. Expand Completeness.
<br>![](/exercises/ex2/images/Ex02_Part03_61_new_3.png)

67. Click 'Create Rule Binding'.
<br>![](/exercises/ex2/images/Ex02_Part03_62_new.png)

68. Click 'Step 2'.
<br>![](/exercises/ex2/images/Ex02_Part03_48.png)

69. Select 'DI_DATA_LAKE'.
<br>![](/exercises/ex2/images/Ex02_Part03_64.png)

70. Click 'Step 3'.
<br>![](/exercises/ex2/images/Ex02_Part03_65.png)

71. Select 'DRUG_NAME' from the 'Mapped to Column' drop down list.
<br>![](/exercises/ex2/images/Ex02_Part03_66.png)

72. Click 'Create Binding'.
<br>![](/exercises/ex2/images/Ex02_Part03_68.png)

73. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part03_69.png)

74. Both rules are now bound to a dataset. Click 'Run All'.
<br>![](/exercises/ex2/images/Ex02_Part03_70.png)

75. Enable 'Save All'.
<br>![](/exercises/ex2/images/Ex02_Part03_71.png)

76. Select 'Replace'.
<br>![](/exercises/ex2/images/Ex02_Part03_72.png)

77. Enable 'Create Linked Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part03_73.png)

78. Click 'Run'.
<br>![](/exercises/ex2/images/Ex02_Part03_74.png)

79. The rules are being evaluated. Wait until the disabled 'View Results' is enabled.
<br>![](/exercises/ex2/images/Ex02_Part03_75.png)

80. Click 'View Results'.
<br>![](/exercises/ex2/images/Ex02_Part03_76.png)

81. The Rule Result window is displayed. Expand the PHARMA_CLAIMS_ENRICHED_## (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part03_77.png)

82. Click 'Details' for the Rule 'DRUG_NAME_VALID_99'.
<br>![](/exercises/ex2/images/Ex02_Part03_78.png)

83. Expand the 'Sample Rows' window.
<br>![](/exercises/ex2/images/Ex02_Part03_80_new.png)

84. You can see a sample of your records.
<br>![](/exercises/ex2/images/Ex02_Part03_82_new.png)

85. Click on 'Failed Rows'. 
<br>![](/exercises/ex2/images/Ex02_Part03_79_new.png)

86. You can see the details about records that did not pass the rules.
<br>![](/exercises/ex2/images/Ex02_Part03_82_new_2.png)

87. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

88. Click 'Home'.
<br>![](/exercises/ex2/images/ClickHome.png)

89. You are back to the Data Intelligence Metadata Explorer home page.
<br>![](/exercises/ex2/images/Ex02_Part03_84.png)

You have now created rules and a rulebook that is evaluating the data quality of your enriched dataset.

## Data Remediation

After completing these steps you will have fixed data quality issues using the data remediation preparation.

1. Click 'View Preparations'.
<br>![](/exercises/ex2/images/Ex02_Part04_01.png)

2. Click 'Preparation for PHARMA_CLAIMS_ENRICHED_##.csv' (where ## is your user number). Note you can always use the 'Filter Preparations' to narrow the results.
<br>![](/exercises/ex2/images/Ex02_Part04_02.png)

3. Notice in the column DRUG_NAME' values of 'Nystatine'.
<br>![](/exercises/ex2/images/Ex02_Part04_03_new.png)

4. Click the header for the column named 'DRUG_NAME'.
<br>![](/exercises/ex2/images/Ex02_Part04_03.png)

5. Click 'Replace'.
<br>![](/exercises/ex2/images/Ex02_Part04_04.png)

6. Type 'Nystatine' for the search string.
<br>![](/exercises/ex2/images/Ex02_Part04_05.png)

7. Type 'Nystatin' for the 'Replace by'.
<br>![](/exercises/ex2/images/Ex02_Part04_05_new.png)

8. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part04_06.png)

9. The value 'Nystatine' was replaced by 'Nystatin'.
<br>![](/exercises/ex2/images/Ex02_Part04_07.png)

10. Notice in the column DRUG_NAME' values of 'Acetaminofen'.
<br>![](/exercises/ex2/images/Ex02_Part04_03_new_2.png)

11. Click 'Replace'.
<br>![](/exercises/ex2/images/Ex02_Part04_08.png)

12. Type 'Acetaminofen' for the search string.
<br>![](/exercises/ex2/images/Ex02_Part04_09.png)

13. Type 'Acetaminophen' for the 'Replace by'.
<br>![](/exercises/ex2/images/Ex02_Part04_09_new.png)

14. Click 'Apply'.
<br>![](/exercises/ex2/images/Apply.png)

15. The value 'Acetaminofen' was replaced by 'Acetaminophen'.
<br>![](/exercises/ex2/images/Ex02_Part04_07_new.png)

16. Click '<' to go back to the 'Rulebook Dataset Results'.
<br>![](/exercises/ex2/images/Ex02_Part04_12.png)

17. Click 'Run Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part04_13.png)

18. Type 'REMEDIATED_DATA_##' for the 'Dataset Name' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_14.png)

19. Click 'Apply'.
<br>![](/exercises/ex2/images/Apply.png)

20. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

21. Click 'Home'.
<br>![](/exercises/ex2/images/ClickHome.png)

You fixed data quality issues using the data preparation recipe that was automatically generated with the execution of your rulebook.
In a normal process, the output dataset resulting of that data remediation process would be used in order to update the original table that contains the data quality issues using workflow and approvals.
For this hands-on, you will use the data preparation recipe you created to simulate the update process of the data and see the results in the rulebook.

22. Click 'View Preparations'.
<br>![](/exercises/ex2/images/Ex02_Part04_01.png)

23. Click 'DRUG_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_18.png)

24. Click 'Recipe'.
<br>![](/exercises/ex2/images/Ex02_Part04_19.png)

25. Edit the 'Enrich' action.
<br>![](/exercises/ex2/images/Ex02_Part04_20.png)

26. Click '+' to add a new source.
<br>![](/exercises/ex2/images/Ex02_Part04_21.png)

27. Click 'Browse'.
<br>![](/exercises/ex2/images/Ex02_Part04_22.png)

28. Select the connection 'DI_DATA_LAKE' from the drop down list.
<br>![](/exercises/ex2/images/Ex02_Part04_23.png)

29. Click 'shared'.
<br>![](/exercises/ex2/images/Ex02_Part04_24.png)

30. Type in '99' in the 'Filter items' search bar (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_25.png)

31. Click 'TechEd_DA264_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_26.png)

32. Click 'REMEDIATED_DATA_##' (where ## is your user number).  Note: You can use the Filter items search to narrow down our results.
<br>![](/exercises/ex2/images/Ex02_Part04_27.png)

33. Click 'OK'.
<br>![](/exercises/ex2/images/Ex02_Part04_28.png)

34. After the dataset is acquired, the remediated dataset will be added to the list of sources.
<br>![](/exercises/ex2/images/Ex02_Part04_29.png)

35. Click 'X' to delete the join with the dataset 'D1'.
<br>![](/exercises/ex2/images/Ex02_Part04_30.png)

36. Drag and drop the 'REMEDIATED_DATA_##' datasource to the left side of 'P1' (where # is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_31.png)

37. Select 'Left Join'.
<br>![](/exercises/ex2/images/Ex02_Part04_32.png)

38. Scroll down and uncheck 'VALID_DRUG' and 'POTENCY' under the 'left source' list of columns.
<br>![](/exercises/ex2/images/Ex02_Part04_33.png)

39. Scroll down and uncheck 'ORIG_PRODUCT', 'DOSAGE', 'ROUTE_ADMINISTERED', and 'NOTES' from the right source list of columns.
<br>![](/exercises/ex2/images/Ex02_Part04_34.png)

40. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part04_35.png)

41. Click 'Apply Enrichment'.
<br>![](/exercises/ex2/images/Ex02_Part04_36.png)

42. Click 'POTENCY_0'.
<br>![](/exercises/ex2/images/Ex02_Part04_37.png)

43. Click 'Rename'.
<br>![](/exercises/ex2/images/Ex02_Part04_38.png)

44. Type 'POTENCY' for the 'New Column Name'.
<br>![](/exercises/ex2/images/Ex02_Part04_39.png)

45. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part04_40.png)

46. Click '<' to come back Actions menu.
<br>![](/exercises/ex2/images/Ex02_Part04_41.png)

47. Click 'Run Preparation'.
<br>![](/exercises/ex2/images/Ex02_Part04_47_new.png)

48. Type 'PHARMA_CLAIMS_CURATED_##' for the 'Dataset Name' (Where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_43.png)

49. Click 'Apply'.
<br>![](/exercises/ex2/images/Ex02_Part04_40.png)

50. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/Ex02_Part02_44.png)

51. Click 'Home'.
<br>![](/exercises/ex2/images/Ex02_Part02_44_ner.png)

52. Click 'rulebooks'.
<br>![](/exercises/ex2/images/Ex02_Part04_46.png)

53. Type '##' in the 'Filter rulebook names' text field (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_47.png)

54. Click 'PHARMA_CLAIMS_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_48.png)

55. Expand 'Accuracy' set of rules.
<br>![](/exercises/ex2/images/Ex02_Part04_49.png)

56 Edit the rules binding associated to the first rule: 'DRUG_NAME_VALID_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_50.png)

57. Delete the rule binding.
<br>![](/exercises/ex2/images/Ex02_Part04_51.png)

58. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part04_52.png)

59. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part04_53.png)

60. Expand 'Accuracy'.
<br>![](/exercises/ex2/images/Ex02_Part04_54.png)

61. Click 'Create Rule Binding'.
<br>![](/exercises/ex2/images/Ex02_Part04_55.png)

62. Click 'Step 2'.
<br>![](/exercises/ex2/images/Ex02_Part04_56.png)

63. Click 'Browse'.
<br>![](/exercises/ex2/images/Ex02_Part04_57.png)

64. Select 'DI_DATA_LAKE' from the 'Connection' drop down list.
<br>![](/exercises/ex2/images/Ex02_Part04_58.png)

65. Click 'shared'.
<br>![](/exercises/ex2/images/Ex02_Part04_59.png)

66. Filter 'Tech*##' and select your folder (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_60.png)

67. Select your 'TechEd_DA264_##' folder (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_60_new.png)

68. Select 'PHARMA_CLAIMS_CURATED_##' (where ## is your user number). Then click 'Step 3'.
<br>![](/exercises/ex2/images/Ex02_Part04_61.png)

69. Click 'Step 3'.
<br>![](/exercises/ex2/images/Ex02_Part04_62_new.png)

70. Select 'VALID_DRUG' for the mapping. Then click 'Create Binding'.
<br>![](/exercises/ex2/images/Ex02_Part04_62.png)

71. Click 'Create Binding'.
<br>![](/exercises/ex2/images/Ex02_Part04_62_new1.png)

72. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part04_63.png)

73. Expand 'Completeness', then edit the rule binding.
<br>![](/exercises/ex2/images/Ex02_Part04_64.png)

74 Edit the rules binding associated to the first rule: 'PHARMA_CLAIMS_ENRICHED_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_50_new.png)

75. Delete the column mapping for 'DRUG_NAME'. 
<br>![](/exercises/ex2/images/Ex02_Part04_65.png)

76. Click 'Save'.
<br>![](/exercises/ex2/images/Ex02_Part04_65_new.png)

77. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part04_66.png)

78. Expand 'Completeness'.
<br>![](/exercises/ex2/images/Ex02_Part04_64.png)

79. Click 'Create Rule Binding'.
<br>![](/exercises/ex2/images/Ex02_Part04_67.png)

80. Click 'Step 2'.
<br>![](/exercises/ex2/images/Ex02_Part04_56.png)

81. Select the existing 'Connection ID' for 'PHARMA_CLAIMS_CURATED_##' (where ## is your user number).
<br>![](/exercises/ex2/images/Ex02_Part04_69.png)

82. Click 'Step 3'.
<br>![](/exercises/ex2/images/Ex02_Part04_69_new.png)

83. Click 'Create Binding'.
<br>![](/exercises/ex2/images/Ex02_Part04_70.png)

84. Click 'Close'.
<br>![](/exercises/ex2/images/Ex02_Part04_71.png)

85. Click 'Run All'.
<br>![](/exercises/ex2/images/Ex02_Part04_72.png)

86. Click 'Run'.
<br>![](/exercises/ex2/images/Ex02_Part04_73.png)

87. Wait for the rulebook execution to finish.
<br>![](/exercises/ex2/images/Ex02_Part04_74.png)

88. You can check the execution completion status with the notification.
<br>![](/exercises/ex2/images/Ex02_Part04_75.png)

89. Click 'View Results'.
<br>![](/exercises/ex2/images/Ex02_Part04_76.png)

90. Click 'Yes'.
<br>![](/exercises/ex2/images/Ex02_Part04_77.png)

91. Expand the dataset.
<br>![](/exercises/ex2/images/Ex02_Part04_78.png)

92. The quality of the data improved.
<br>![](/exercises/ex2/images/Ex02_Part04_79.png)

93. Click 'Data Intelligence Metadata Explorer'. 
<br>![](/exercises/ex2/images/ClickDI.png)

93. Click 'Home'.
<br>![](/exercises/ex2/images/ClickHome.png)

94. You are back to the home page of the Metadata Explorer.
<br>![](/exercises/ex2/images/Ex02_Part04_81.png)

You have now fixed data quality issues using the data remediation preparation.

## Conclusion

In this hands-on you:
* Accessed and discovered several data repositories (Database, Cloud Data Lake, Local File System)
* Profiled and published dataset to the catalog
* Found data quality issues
* Created your own enriched dataset
* Created a glossary and terms and associated them with your data
* Assessed the quality of a dataset using rules and a rulebook
* Improved the data with data remediation and witness the results

For more information about SAP Data Intelligence, you can have a look at the following ressources:
* Product Home Page: https://www.sap.com/products/data-intelligence/features.html
* Help Portal: https://help.sap.com/viewer/product/SAP_DATA_INTELLIGENCE/Cloud/en-US

Thanks!
