YAMNet Weather Validation Interface for Soundscape Analysis

The following scripts allow you to run YAMNet to detect weather events and validate the results. 
The scripts were used in the manuscript: Sangermano,  Weijerman, Nawaz,  Al-Abdulwahab Hyper-arid soundscapes: an exploratory study of bioacoustics indices in Saudi Arabia.
When using this code for analysis please cite: 

YAMNet Code: Google Research & TensorFlow Authors. (2020).YAMNet: A deep net for audio event classification [Computer software]. GitHub repository. https://github.com/tensorflow/models/tree/master/research/audioset/yamnet
YAMNet Architecture: Gemmeke, J. F., Ellis, D. P. W., Freedman, D., Jansen, A., Lawrence, W., Moore, R. C., Plakal, M., & Ritter, M. (2017).  Audio Set: An ontology and human-labeled dataset for audio events.  
In ICASSP 2017 (pp. 776–780). IEEE. https://doi.org/10.1109/ICASSP.2017.7952261

This code: Sangermano, F. (2026). YAMNet Weather Validation Interface for Soundscape Analysis. GitHub Repository. https://github.com/flosanger/WeatherEvents/ .

This repository has the codes needed to 
1) Identify the presence of weather events including YAMNet lables: Rain, Rain on surface, Raindrop, Wind, and Wind noise (microphone)
2) Use the results of the weather detection to generate a random sample of recordings, move recordings used for validation to a separate folder, and generate an HTML validation sheet that allows the user to listen and visualise each sampled recording in Audacity, select a validation label, and make notes.

3) The code is intended to facilitate the process of identifying and validating weather events that need tobe exluded from soundscape analysisbefore the calcuation of acoustic indices.

How to run:

1- Run Yamnet_OnlyDetectWeather. This python script generates a CSV file including information of the filename with its path, the class of weather event extracted,the number of chunks within the recording that identified as a weather event, the percentage of chunks assessed that were a weather event, and the maximum per class confidence.  
Before running change the input and output paramters: 
# =====================================================
# INPUT / OUTPUT
# =====================================================

audio_folder = r"D:/Flor/SaudiArabia/Data/WavsChannel60" --> this is the folder that contains your wav files
output_csv = r"D:/Flor/SaudiArabia/YamnetResults/weather_labels_summaryWithConfidence.csv" --> folder and name of your output table.


2- Run SamplesWeather. This python script samples the result of 1) extracting 100 random recordings with no weather detected and 100 random recordings where weather was detected distributed across the maximum confidence level of any event detected. 
Before running change 
# Load your CSV
df = pd.read_csv("D:\Flor\SaudiArabia\YamnetResults\weather_labels_summaryWithConfidence.csv") --> output from step 1

# Save to CSV
final_sample.to_csv(r"D:\Flor\SaudiArabia\YamnetResults\sampled_files_Final.csv", index=False) --> name of csv to save the list of sampled files
# Folder where files will be copied
output_folder = r"D:\Flor\SaudiArabia\YamnetResults\forvalidation_Final" --> folder where selected files will be copied to.
# html output file
html_file = r"D:\Flor\SaudiArabia\YamnetResults\validation_page_final.html" --> name and location of output HTML that will be used to explore data for validation

-- and within the HTML code: 
        a.download = r"D:\Flor\SaudiArabia\YamnetResults\validation_resultsFinal.csv"; --> location and name of the file created after clicking save to csv
         a.download = r"D:\Flor\SaudiArabia\YamnetResults\validation_page_with_editsFinal.html"; --> location and name of the file created after clicking save to HTML
