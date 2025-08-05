# Groundwater Converter User Manual  
### 1	GENERAL SETUP  
#### 1.1	INSTALLATION  
Step 1: From Python.org download [Python](https://www.python.org/downloads/). Run the installer as it will put it into your Windows Programs files automatically. (Only need to do this once on a new computer.)  

Step 2: With the converter downloaded to your desktop, documents, or some other useful folder, a little setup is required to begin use. First, within the Groundwater Converter v1.1.2 file, find the folder “outputFiles” and folder “finaloutput”, and below the folders find the “analytenames” and “analytenamesremoved” csv files and the “Groundwater Converter v1.1.2” exe. Create shortcuts for these and move (drag) them into the master “Groundwater Converter” folder. Everything you need to do can be accessed by these 5 files.  

#### 1.2	DOWNLOADING DATABASES  
##### 1.2.1	Water Quality Portal  
  To acquire data for the WQP, go to https://www.waterqualitydata.us and using advanced (not basic) select the relevant country, state, and county. Under Site Type select “Aggregate groundwater use (NWIS, STORET)”, “Spring (NWIS, STORET)”, and “Well (NWIS, STORET)”. Under Sample Media select “Water (NWIS, STEWARDS, STORET)”. Under Characteristic Group, select all Inorganics (Major, Minor, Metal, Non-Metal), Nutrient, Physical, and Radiochemical. Under Download the Data keep all data source types. Under File Format select Comma-Separated. Under Data Profiles first download (button at bottom of page) “Site Data Only” and then “Sample Results (physical/chemical metadata)”. These are your two necessary data files for the WQP. Ensure that the “Site Data” file has station somewhere in the name and that “Sample Results” file has Result somewhere in the name.  
##### 1.2.2	ECMC/COGCC  
  To acquire data for the ECMC (formerly COGCC), first navigate to the Downloads tab and in the Environmental section select the Analytical Sample Data (Updated Monthly). Here click on the Water Well Download or just click [here](https://ecmc.state.co.us/documents/data/downloads/environmental/WaterWellDownload.html) to jump to that page. Extract all files from the zipped folder into your project folder/subfolder. Note: Groundwater sources may include domestic water wells, irrigation wells, stock wells, commercial wells, seeps, or springs. When opening the “WaterWellDownload” Access file which contains macros blocked by Microsoft, click enable and trust.  
Double click on “BasicQuery” under “DL Locations” to open the table, then right click on “BasicQuery” under “DL Locations” to open the dropdown menu. Select “Design View”. You should see a table with the already present columns. Scroll to the right to the first empty column, then add, in order (do second row first “DL_Locations to get proper menu for first row), “County” from DL_Locations, then “Facilility Type” from DL_Locations, and finally “WellDepth” from DL_Locations.  
You can now move on to export the file: Right click on tab header “BasicQuery” and select “Save”. Navigate to the top tab “External Data” and then “Text File” from the top menu banner. First, select your file location and change the file extension in the “File Name” box to .csv, then select “OK”. Now, ensure “Delimited” is selected before selecting “Next” again. Ensure the delimiter is selected as “Comma” and check the box “Include Field Names on First Row” box, select “Next”. Finally, ensure you’re saving your file to the right folder (your input folder for the groundwater converter), and select “Finish”. You can then close Access.  
##### 1.2.3	Colorado Department of Agriculture  
  Find the new CDA web portal [here](https://awqp.erams.com/filters). In the portal, there are several options for you to select your area. You are looking to generate 5 files. Detect and nondetect files for "inorganics" and "nutrients", and an "other" file.  
  
  Start by selecting your county. Under *Filter by Area*, select "Known Boundaries" For *Type of Boundary*, select "Counties". For *Boundary*, choose your desired county.  

  For *Site Group*, choose "Groundwater" to avoid any surface sensors. You can ignore *Groundwater Use*, *Site Type*, and *Monitoring Region*.  

  To specify our five categories, we are going to change two categories, *Analyte - Filter 1* and *Detection Level* You can ignore *Analyte - Filter 2*, *Analyte - Filter 3*, *Analyte Name*, *Site Name*, *Site ID*, *Year*, and *Date Range*.  

  We want to generate 5 files, Inorganic Detects, Inorganic Nondetects, Nutrient Detects, Nutrient Nondetects, and Physical. 

  For inorganics, under *Analyte - Filter 1* select "Inorganics, Metal", "Inorganics, Non-Metal", and "Radiochemical". If "Radiochemical" does not show up, there are no results in your area for them. Simply ignore them and move on with the inorganics.
  For detects, select "Detected" for *Detection Level*. Save this file as "inorganicdetects.xlsx" or something of the like.
  For nondetects, select "Nondetected" for *Detection Level*. Save this file as "inorganicnondetects.xlsx" or something of the like.

  For nutrients, under *Analyte - Filter 1* select "Nutrients".
  For detects, select "Detected" for *Detection Level*. Save this file as "nutrientdetects.xlsx" or something of the like.
  For nondetects, select "Nondetected" for *Detection Level*. Save this file as "nutrientdetects.xlsx" or something of the like.

  For physical data, under *Analyte - Filter 1* select "Physical". Leave *Detection Level* blank. Save this file as "physical.xlsx" or something of the like.
  
  For each download, you will recieve a .xlsx file. This will need to be saved as a .csv for the program to function. Open the file using microsoft excel, and select *Save As* in the menu (Select *File* in the top left). For filetype, select "CSV (Comma Delimited) *.csv" Make sure you do not select a different CSV format like Macintosh or UTF-8. The files are now ready for the converter!
### 2	RUNNING THE PROGRAM  
#### 2.1	STARTUP  
  To begin, run the previously generated “Groundwater Converter v1.1.1 – Shortcut” by double clicking. Two windows should open, a console in the background and a blue GUI in front. On top of the GUI screen, click browse next to Folder. Select the folder where your raw database files are located.  
#### 2.2	FORMATTING DIFFERENT DATABASES  
##### 2.2.1	Water Quality Portal  
  For the Water Quality Portal, you should have a “results” and “station” csv downloaded from their website. Upload the two desired files using the “Upload Primary Files Here” upload slots and change the default “Data Source” to “Water Quality Portal” in the “Select Data Source” box. Click run, and you should have your outputs.  
##### 2.2.2	Colorado Oil and Gas Conservation Commission  
  For the Oil and Gas Conservation Commission, you should have 1 file, for formatting tips see above in 1.2.2. Upload your file using a primary upload slot. Select COGCC under data source and be sure to manually add in your county in the desired county. Select run to get your outputs. (If no data exists for that county, ignore this step.)  

##### 2.2.3	Colorado Department of Agriculture  
  For the Colorado Department of Agriculture, you should have 5   files, for formatting tips, see above in 1.2.3. Upload all five files using all five upload slots, select CDA under data source, and click run to get the outputs. (If no data exists for that county, ignore this step.)  
#### 2.3	MERGING THE DATASETS  
When you have created all the final outputs (up to 3 well detects, 3 well non-detects, 2 spring detects, 2 spring non-detects) and are ready to create a final output file, select the merge outputs button. Keep in mind, if you make any changes to analytenames.csv or the code of the Python script files, you must run the GroundWaterConverter again for the files you changed and must merge the datasets again. Finally, move or copy all the final output files into your project file location. Note should you not need all the cross-tabbed analytes, you delete them in the final output files. This is the simplest way to remove analytes.  
# 3	EDITING THE ANALYTE DATA  
#### 3.1	ADDING FORMATTED NAMES  
  With your shortcut to analyte data created, use it to access the csv. Here, you can see the list of all important analyte names. Cross reference your final output for all column names. If any of these names are not in the right format, insert or find that unformatted name in the csv, and add the new name to the newNames column. It may be necessary to check outputFIles to determine which database the unformatted column name came from.  
#### 3.2	REMOVING UNWANTED ANALYTES  
##### 3.2.1	Water Quality Portal  
  For the WQP, there are no unwanted analytes, you should not need to remove any.  
##### 3.2.2	Colorado Oil and Gas Conservation Commission
  For the COGCC, ensure any wanted analytes are in the “analytenames” file. They will not be included otherwise. To remove one that is already included, simply remove the entry from the analyte names file  for that analyte.
##### 3.2.3	Colorado Department of Agriculture
For the CDA, add your desired removal analytes to the end of the dndlist for loop (line 115) in the same format as the image. You could, for example, copy the line of code: if j==’Carbon’:, i.append(‘Carbon’) and move it below. Then, replace the name “Carbon” with whatever analyte you wish to remove.
