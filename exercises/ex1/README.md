# Hands-on - Part 1 (Discover, Prepare, and Enrich)

As a Business Analyst, you want to discover, understand, and gain insight into your data. After accessing various data, profiling the data, and reviewing the profiling results you will be able to add a glossary term, with custom attributes, to a column in your dataset as well as provide a rating and comment on the dataset.

In this exercise, you will discover and interact with various connected systems, upload a dataset, profile the data, rate dataset, create a relationship with data and a glossary term

## Dataset Overview

The first dataset, contains information about pharmaceutic claims for an insurance company and is already stored in a HANA system.

It contains 8 fields:
* RECORD_ID (Unique Identifier associated to a claim)
* INSURANCE (Name of the insurance company)
* PLAN (Plan associated at the insurance company)
* PATIENT_ID (Unique Identifier of the patient this claim is for)
* OUTSTANDING (Amount for the drug)
* CO_PAY (Amount of co pay, if any)
* VISIT (Date of the visit associated to this claim)
* DRUG_NAME (Drug name for the claim)

The second dataset, DRUG__##.csv, is the flat file you retrieved (and renamed) and saved to your desktop.  This file contains a list of drugs which are supported by this insurance company (where ## is your user number).

It contains 6 fields:
* ORIG_PRODUCT (Non split entry)
* DRUG_NAME (Drug name)
* POTENCY (Potency associated to the drug)
* DOSAGE (Dosage for the drug)
* ROUTE_ADMINISTERED (How the drug is administered)
* NOTES (Additional notes, if any)

This hands on will focus on discovering these datasets, find patterns and data quality issues, and fix them.

## Log Into SAP Data Intelligence

After completing these steps, you will have logged into SAP Data Intelligence.

1. Open Chrome and go to the [SAP Data Intelligence](https://vsystem.ingress.dh-1581x4vwrroy.di-xm8.shoot.live.k8s-hana.ondemand.com/login/?redirectUrl=%2Fapp%2Fdatahub-app-launchpad%2F&tenant=default).
<br>![](/exercises/ex1/images/Ex01_Part01_01.png)

2. Enter 'default' for Tenant Name depending on your session and click 'Proceed'.
<br>![](/exercises/ex1/images/Ex01_Part01_02_new.png)

3. Enter the Username that was assigned to you (e.g. 'teched-da264-##'), for Username.
Note: 
* where ## is the number assigned to you.
* If your user number is 99 then your login is 'teched-da264-99'.<br>![](/exercises/ex1/images/Ex01_Part01_03_new.png)

4. Enter the Password that was assigned to you, for your Password.
<br>![](/exercises/ex1/images/Ex01_Part01_04_new.png)
  
5. Click 'Sign In'.
<br>![](/exercises/ex1/images/Ex01_Part01_05_new.png)

4. You are now signed in the application.
<br>![](/exercises/ex1/images/Ex01_Part01_06_new.png)

You have successfully logged into SAP Data Intelligence.

## Browse data in a Connected System (Database)

After completing these steps you will have discovered dataset stored in a database.

1. Click on 'Metadata Explorer'.
<br>![](/exercises/ex1/images/Ex01_Part03_01_new.png)

2. Click on 'Browse Connections'.
<br>![](/exercises/ex1/images/Ex01_Part03_02.png)

3. You are currently viewing a connections in a Grid View layout. Click 'List View'.
<br>![](/exercises/ex1/images/Ex01_Part03_03.png)

4. This allows you to view a list of connections.  Click '...' (More Actions) for 'HANA_DEMO'.
<br>![](/exercises/ex1/images/Ex01_Part03_04.png)

5. Select 'View Capabilities' for the 'HANA_DEMO' connection.
<br>![](/exercises/ex1/images/Ex01_Part03_05.png)

6. This lists all the features supported for a given connected system.
<br>![](/exercises/ex1/images/Ex01_Part03_06.png)

7. Click 'Grid View' to come back to tiles.
<br>![](/exercises/ex1/images/Ex01_Part03_07.png)

8. Click on the 'HANA_DEMO' tile.
<br>![](/exercises/ex1/images/Ex01_Part03_08.png)

9. Select 'TECHED_DA264'.
<br>![](/exercises/ex1/images/Ex01_Part03_09.png)

10. The list of all available tables within the schema shows up.   
<br>![](/exercises/ex1/images/Ex01_Part03_10.png)

11. Type 'PHARMA_CLAIMS_##' in the 'Filter items' text field (where ## is your user number, for example if your user number is 99, then type 'PHARMA_CLAIMS_99').
<br>![](/exercises/ex1/images/Ex01_Part03_11.png)

12. Click 'View FactSheet' on the 'PHARMA_CLAIM_##' database table tile (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part03_12.png).

13. This shows the 'Fact Sheet'.
<br>![](/exercises/ex1/images/Ex01_Part03_13.png)

The 'Fact Sheet' is the central place in SAP Data Intelligence Metatadata Explorer to find information about your data.

You can easily profile the data and get access to metadata information. It also contains links and information about business terms and tags associated to the dataset or the columns. Users can describe, rate, and comment on the data collaboratively. You can preparare the data for other downstream usage.

14. Click 'Start Profiling'.
<br>![](/exercises/ex1/images/Ex01_Part03_14.png)

15. Click 'Yes'.
<br>![](/exercises/ex1/images/Ex01_Part03_15.png)

16. Click 'Notification'.
<br>![](/exercises/ex1/images/Ex01_Part03_16.png)

17. This shows the details of the notifications. Click anywhere outside the notification window to continue interacting with the application.
<br>![](/exercises/ex1/images/Ex01_Part03_17.png)

18. Wait for the profiling task to finish, this action can take some time. You can click 'Refresh' until you see a notification that the profiling is complete or if you see the factsheet now states 'Profiled'. Click 'Refresh' after profiling is complete to see the profiling results.
<br>![](/exercises/ex1/images/Ex01_Part03_18.png)
<br>![](/exercises/ex1/images/Ex01_Part03_18_addition.png)

19. The factsheet was updated with the profiling information once the task is done.
<br>![](/exercises/ex1/images/Ex01_Part03_19.png)

20. Click 'Columns'.
<br>![](/exercises/ex1/images/Ex01_Part03_20.png)

21. Select the Line for 'DRUG_NAME'.
<br>![](/exercises/ex1/images/Ex01_Part03_21.png)

22. Observe 'Data Preview' and the 'Top 10 Distinct Values'.
<br>![](/exercises/ex1/images/Ex01_Part03_22.png)

23. Scroll to the bottom of 'Data Preview'. We can see there are data quality issues such as spelling mistakes on the drug names.
<br>![](/exercises/ex1/images/Ex01_Part03_23.png)

24. Looking at the 'Top 10 Distinct Values', we can see there is a large percentage of null values in the dataset.
<br>![](/exercises/ex1/images/Ex01_Part03_24.png)

25. Click 'Data Intelligence Metadata Explorer'.
<br>![](/exercises/ex1/images/ClickDI.png)

26. Click 'Home'.
<br>![](/exercises/ex1/images/ClickHome.png)

You have now discovered a table in a database, profiled the data, and found some data quality issues.

## Upload your Dataset

After completing these steps you will have uploaded a dataset from a flat flat to a cloud data lake data repository using SAP Data Intelligence.

1. Click on 'Browse Connections'.
<br>![](/exercises/ex1/images/Ex01_Part02_01.png)

2. Click on the 'DI_DATA_LAKE' tile.
<br>![](/exercises/ex1/images/Ex01_Part02_02.png)

3. Click on the 'shared' tile.
<br>![](/exercises/ex1/images/Ex01_Part02_03.png)

4. Click on the New Folder icon (folder with a +).
<br>![](/exercises/ex1/images/Ex01_Part02_04.png)

5. Enter 'TechEd_DA264_##' for folder name (where ## is the number assigned to you).
<br>![](/exercises/ex1/images/Ex01_Part02_05.png)

6. Click 'OK'.
<br>![](/exercises/ex1/images/Ex01_Part02_06.png)

7. Search for 'TechEd_DA264_##' to isolate your newly created folder, then click on your newly added 'TechEd_DA264_##' folder (where ## is the number assigned to you).
<br>![](/exercises/ex1/images/Ex01_Part02_07.png)

8. Upload a file, click on the 'Upload Files' icon on the toolbar.
<br>![](/exercises/ex1/images/Ex01_Part02_08.png)

9. Click on 'Upload' in the upper right hand corner of the Upload Files pop-up window.
<br>![](/exercises/ex1/images/Ex01_Part02_09.png)

10. Browse to your Desktop, where you downloaded and extracted 'DRUG_##.csv' (where ## is the number assigned to you) and select it.
<br>![](/exercises/ex1/images/Ex01_Part02_10.png)

11. Click 'Open'.
<br>![](/exercises/ex1/images/Ex01_Part02_11.png)

12. Click 'Upload'.
<br>![](/exercises/ex1/images/Ex01_Part02_12.png)

13. The file will upload on the data lake.
<br>![](/exercises/ex1/images/Ex01_Part02_13.png)

14. After Upload is Complete, click 'Close'.
<br>![](/exercises/ex1/images/Ex01_Part02_14.png)

15. The file is now uploaded and available in the data lake.
<br>![](/exercises/ex1/images/Ex01_Part02_15.png)

You have now uploaded a dataset from a flat file on your local system to a cloud data lake data repository using SAP Data Intelligence Metadata Explorer.

## Enrich Dataset and Isolate Data Quality Issues

After completing these steps you will have created a new dataset using self-service data preparation.
This new dataset will help to easily isolate invalid claims.
Additionally you will profile this dataset, add a rating and description and publish it in the catalog so it can be easily retrieved.

1. Click 'More Actions'.
<br>![](/exercises/ex1/images/Ex01_Part04_01.png)

2. Select 'Prepare Data'.
<br>![](/exercises/ex1/images/Ex01_Part04_02.png)

3. The self-service data preparation appears.
<br>![](/exercises/ex1/images/Ex01_Part04_03.png)

4. The first record of the data is actually the column header.
<br>![](/exercises/ex1/images/Ex01_Part04_04.png)

5. On the bottom right, check 'Use first row as header'.
<br>![](/exercises/ex1/images/Ex01_Part04_05.png)

6. Click 'Continue'.
<br>![](/exercises/ex1/images/Ex01_Part04_06.png)

7. The application will automatically recreate a new sample with the updated metadata structure.
<br>![](/exercises/ex1/images/Ex01_Part04_07.png)

8. The dataset now has the proper header.
<br>![](/exercises/ex1/images/Ex01_Part04_08.png)

9. Click 'Actions'.
<br>![](/exercises/ex1/images/Ex01_Part04_09.png)

10. Click 'Enrich Preparation'.
<br>![](/exercises/ex1/images/Ex01_Part04_10.png)

11. You are now able to enrich and prepare your data.
<br>![](/exercises/ex1/images/Ex01_Part04_11.png)

12. Click '+' to add a new source of data to merge with your csv file.
<br>![](/exercises/ex1/images/Ex01_Part04_12.png)

13. Click 'Browse'.
<br>![](/exercises/ex1/images/Ex01_Part04_13.png)

14. Select 'HANA_DEMO as a 'Connection'.
<br>![](/exercises/ex1/images/Ex01_Part04_14.png)

15. Click 'TECHED_DA264'.
<br>![](/exercises/ex1/images/Ex01_Part04_15.png)

16. Type 'CLAIMS_##' in the 'Filter items' text field (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_16.png)

17. Select 'PHARMA_CLAIMS_##' (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_17.png)

18. Click 'OK'.
<br>![](/exercises/ex1/images/Ex01_Part04_18.png)

19. The application is acquiring a sample of the selected PHARMA_CLAIMS_## dataset (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_19.png)

20. The selected PHARMA_CLAIMS_## dataset can now be used to merge data (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_20.png)

21. Drag and drop 'PHARMA_CLAIMS_##' on the cell on the left hand-side of the main dataset (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_21.png)

22. Select 'Left Join'.
<br>![](/exercises/ex1/images/Ex01_Part04_22.png)

23. Scroll down the list of output columns and uncheck 'ORIG_PRODUCT', 'POTENCY', 'DOSAGE', 'ROUTE_ADMINISTERED', and 'NOTES'.
<br>![](/exercises/ex1/images/Ex01_Part04_23.png)

24. Click Apply.
<br>![](/exercises/ex1/images/Ex01_Part04_24.png)

25. You will now see a preview of the merged data.
<br>![](/exercises/ex1/images/Ex01_Part04_25.png)

26. The merged data now shows a null value for the column 'DRUG_NAME_0' when a record from the claim data is for a drug that is not listed in the list of supported drugs.
<br>![](/exercises/ex1/images/Ex01_Part04_26.png)

27. Click 'Apply Enrichment' to confirm the join/merge action.
<br>![](/exercises/ex1/images/Ex01_Part04_27.png)

28. You are now back on the main self-service data preparation, where you can see enriched (merged) dataset.
<br>![](/exercises/ex1/images/Ex01_Part04_28.png)

The enriched dataset now contains null values for the field 'DRUG_NAME_0' for the records in the PHARMA_CLAIMS dataset which the drug name did not exists in our reference.

There are potential multiple reasons for that. Some reasons might be spelling mistakes of drug names or drugs that are not taken into account by the insurance company or the drug name in our claim was null.

You can now use this enriched dataset to isolate the data quality issues to further understand the data.

29. Click 'Actions'.
<br>![](/exercises/ex1/images/Action_prep.png)

30. Click 'Add Columns'.
<br>![](/exercises/ex1/images/Ex01_Part04_30.png)

31. Type 'ValidClaim' for the 'Column Name'.
<br>![](/exercises/ex1/images/Ex01_Part04_31.png)

32. Click 'Expression'.
<br>![](/exercises/ex1/images/Ex01_Part04_32.png)

33. Type the following expression: 'CASE WHEN "DRUG_NAME_0" IS NULL THEN 'NO' ELSE 'YES' END'.
<br>![](/exercises/ex1/images/Ex01_Part04_33.png)

34. Click 'OK'.
<br>![](/exercises/ex1/images/Ex01_Part04_34.png)

35. Click 'Apply'(at the bottom right).
<br>![](/exercises/ex1/images/Apply.png)

36. A new column, ValidClaim' is now created.
<br>![](/exercises/ex1/images/Ex01_Part04_36.png)

37. Select the column 'DRUG_NAME_0'.
<br>![](/exercises/ex1/images/Ex01_Part04_37.png)

38. Click 'Remove'.
<br>![](/exercises/ex1/images/Ex01_Part04_38.png)

39. The column 'DRUG_NAME_0' has been deleted.
<br>![](/exercises/ex1/images/Ex01_Part04_39.png)

40. Click '<' to navigate back to the 'Actions' menu.
<br>![](/exercises/ex1/images/Ex01_Part04_40.png)

41. Click 'Run Preparation'.
<br>![](/exercises/ex1/images/RunPreparation.png)

42. Type 'PHARMA_CLAIMS_ENRICHED_##' (where ## is your user number) for the 'Dataset Name'.
<br>![](/exercises/ex1/images/Ex01_Part04_42.png)

43. Click 'Apply'(at the bottom right).
<br>![](/exercises/ex1/images/Apply.png)

44. Click 'Data Intelligence Metadata Explorer'.
<br>![](/exercises/ex1/images/Ex01_Part04_44.png)

45. Select 'Monitor'.
<br>![](/exercises/ex1/images/Ex01_Part04_45.png)

46. Click 'Monitor Tasks'.
<br>![](/exercises/ex1/images/Ex01_Part04_45_new.png)

47. 'Monitoring' shows the current running tasks. Wait for your task to complete.
<br>![](/exercises/ex1/images/Ex01_Part04_46.png)

48. The task is completed.
<br>![](/exercises/ex1/images/Ex01_Part04_47.png)

49. Click 'Data Intelligence Metadata Explorer'.
<br>![](/exercises/ex1/images/ClickDI.png)

50. Click 'Home'.
<br>![](/exercises/ex1/images/ClickHome.png)

51. Click 'Browse Connections'.
<br>![](/exercises/ex1/images/Ex01_Part02_01.png)

52. Click 'DI_DATA_LAKE'.
<br>![](/exercises/ex1/images/Ex01_Part02_02.png)

53. Click 'shared'.
<br>![](/exercises/ex1/images/Ex01_Part02_03.png)

54. Type '*_##' (where ## is your user number) in the Filter field.
<br>![](/exercises/ex1/images/Ex01_Part04_52.png)

55. Click TechEd_DAT163_## (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_53.png)

56. Click 'More Actions' ('...') newly created dataset named PHARMA_CLAIMS_ENRICH_## (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_54.png)

57. Select 'View Fact Sheet'.
<br>![](/exercises/ex1/images/Ex01_Part04_55.png)

57. Click 'Overview'.
<br>![](/exercises/ex1/images/Ex01_Part04_55_new.png)

58. The Fact Sheet for the dataset is not profiled and has not been published.
<br>![](/exercises/ex1/images/Ex01_Part04_56.png)

59. Click the 'Profiling' icon.
<br>![](/exercises/ex1/images/Ex01_Part04_57.png)

60. Click 'Yes'.
<br>![](/exercises/ex1/images/Ex01_Part04_58.png)

61. Wait for the profiling to be executed (there will be two notifications which you can check by clicking on the notification icon). Then Click 'Refresh'.
<br>![](/exercises/ex1/images/Ex01_Part04_59.png)

62. The dataset is now profiled.
<br>![](/exercises/ex1/images/Ex01_Part04_60.png)

63. Click '<' to come back to the connection browser.
<br>![](/exercises/ex1/images/Ex01_Part04_61.png)

64. Click 'More Actions' ('...') for PHARMA_CLAIMS_ENRICHED_## (where ## is your user number).
<br>![](/exercises/ex1/images/Ex01_Part04_62.png)

65. Click 'New Publication'.
<br>![](/exercises/ex1/images/Ex01_Part04_63.png)

66. Type 'Pharma Claims Publication ##' (where ## is your user number) for the 'Name' text field. 
<br>![](/exercises/ex1/images/Ex01_Part04_64.png)

67. Type 'Publication for enriched claimed data' for the 'Description' text field.
<br>![](/exercises/ex1/images/Ex01_Part04_64_new.png)

68. Click 'Publish'.
<br>![](/exercises/ex1/images/Ex01_Part04_65.png)

69. The application sends a notification for the publication task trigger.
<br>![](/exercises/ex1/images/Ex01_Part04_66.png)

70. The application sends another notification when the publication task is finished.
<br>![](/exercises/ex1/images/Ex01_Part04_67.png)

71. Click 'Refresh'.
<br>![](/exercises/ex1/images/Ex01_Part04_68.png)

72. You can now see that the dataset is both profiled and published in the application catalog.
<br>![](/exercises/ex1/images/Ex01_Part04_69.png)

70. Click 'View Fact Sheet'.
<br>![](/exercises/ex1/images/Ex01_Part04_70.png)

71. Click 'Reviews'.
<br>![](/exercises/ex1/images/Ex01_Part04_71.png)

72. Click the stars icon to post a rating.
<br>![](/exercises/ex1/images/Ex01_Part04_72.png)

73. Click and define a rating (for example 4 stars rating is done by clicking the 4th star).
<br>![](/exercises/ex1/images/Ex01_Part04_73.png)

74. Add a comment: 'This dataset helps to easily identify claims for drugs that are not compliant'.
<br>![](/exercises/ex1/images/Ex01_Part04_74.png)

75. Click 'OK'.
<br>![](/exercises/ex1/images/Ex01_Part04_75.png)

76. The dataset has been enriched with a rating and a comment.
<br>![](/exercises/ex1/images/Ex01_Part04_76.png)

77. Click 'Data Intelligence Metadata Explorer' and Click 'Home'.
<br>![](/exercises/ex1/images/Ex01_Part04_77.png)

78. You returned to the Metadata Explorer home page.
<br>![](/exercises/ex1/images/Ex01_Part04_78.png)

You have now created a new dataset by merging two datasets using self-service data preparation. This new dataset helps to easily isolate invalid pharmaceutical claims.
You also profiled this dataset, added a rating and a description, and published the dataset in the catalog so it can be easily retrieved.

## Summary

You've now used Metadata Explorer to connect and interact with different data repositories (Databases, Cloud Data Lake, Local File System). You profiled and discovered data to identify data quality issues. You created a new enriched dataset to isolate these data quality issues. You published this dataset to the catalog.

Continue to - [Hands-on - Part 2: Govern and Monitor Data Quality](../ex2/README.md)
