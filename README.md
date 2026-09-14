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

1- Run Yamnet_onl
