<h1 style="font-size:32px; font-weight:700;">YAMNet Weather Validation Interface for Soundscape Analysis</h1>

<p>
This repository contains Python tools for detecting and validating weather‑related acoustic events using <strong>YAMNet</strong>, with the goal of removing weather‑affected recordings prior to ecoacoustic index calculation.
</p>

<p>
These scripts were used in the manuscript:<br>
<strong>Sangermano, F., Weijerman, M., Nawaz, R., & Al‑Abdulwahab, S. (2026).<br>
<i>Hyper‑arid soundscapes: an exploratory study of bioacoustic indices in Saudi Arabia.</i></strong>
</p>

<hr>

<h2>Citations</h2>

<h3>YAMNet Code</h3>
<p>
Google Research & TensorFlow Authors. (2020).<br>
<i>YAMNet: A deep net for audio event classification</i> [Computer software].<br>
GitHub repository: 
<a href="https://github.com/tensorflow/models/tree/master/research/audioset/yamnet">
https://github.com/tensorflow/models/tree/master/research/audioset/yamnet
</a>
</p>

<h3>YAMNet Architecture / Training Dataset</h3>
<p>
Gemmeke, J. F., Ellis, D. P. W., Freedman, D., Jansen, A., Lawrence, W., Moore, R. C., Plakal, M., & Ritter, M. (2017).<br>
<i>Audio Set: An ontology and human‑labeled dataset for audio events.</i><br>
In <i>ICASSP 2017</i> (pp. 776–780). IEEE.<br>
<a href="https://doi.org/10.1109/ICASSP.2017.7952261">https://doi.org/10.1109/ICASSP.2017.7952261</a>
</p>

<h3>This Repository</h3>
<p>
Sangermano, F. (2026).<br>
<i>YAMNet Weather Validation Interface for Soundscape Analysis.</i><br>
GitHub repository: 
<a href="https://github.com/flosanger/WeatherEvents/">
https://github.com/flosanger/WeatherEvents/
</a>
</p>

<hr>

<h2>Overview</h2>

<h3>1. Detect weather events using YAMNet</h3>
<p>The script identifies the following YAMNet weather classes:</p>
<ul>
  <li>Rain</li>
  <li>Rain on surface</li>
  <li>Raindrop</li>
  <li>Wind</li>
  <li>Wind noise (microphone)</li>
</ul>

<p>The output CSV includes:</p>
<ul>
  <li>Filename and full path</li>
  <li>Detected weather class</li>
  <li>Number of chunks flagged as weather</li>
  <li>Percent of chunks flagged</li>
  <li>Maximum confidence across detected classes</li>
</ul>

<h3>2. Generate a validation dataset and HTML interface</h3>
<p>The second script:</p>
<ul>
  <li>Samples <strong>100 clean recordings</strong> (no weather detected)</li>
  <li>Samples <strong>100 weather‑affected recordings</strong>, stratified by maximum confidence</li>
  <li>Copies sampled files into a validation folder</li>
  <li>Generates an HTML validation sheet allowing the user to:
    <ul>
      <li>Listen to each recording</li>
      <li>Open the file directly in Audacity</li>
      <li>Select a validation label</li>
      <li>Write notes</li>
      <li>Export results to CSV</li>
      <li>Save the HTML with edits</li>
    </ul>
  </li>
</ul>

<h3>3. Facilitate weather‑event removal prior to ecoacoustic analysis</h3>
<p>
This workflow helps ensure that weather‑affected recordings are excluded before computing acoustic indices, improving the reliability of soundscape analyses.
</p>

<hr>

<h2>How to Run the Workflow</h2>

<h3>Step 1 — Run <code>Yamnet_OnlyDetectWeather.py</code></h3>
<p>This script processes all WAV files and produces a CSV summarizing YAMNet weather detections.</p>

<p>Before running, update:</p>

<pre>
audio_folder = r"D:/Flor/SaudiArabia/Data/WavsChannel60"
output_csv = r"D:/Flor/SaudiArabia/YamnetResults/weather_labels_summaryWithConfidence.csv"
</pre>

<h3>Step 2 — Run <code>SamplesWeather.py</code></h3>
<p>This script:</p>
<ul>
  <li>Loads the CSV from Step 1</li>
  <li>Samples 200 recordings (100 clean + 100 weather)</li>
  <li>Copies sampled files to a validation folder</li>
  <li>Generates the HTML validation interface</li>
</ul>

<p>Update the following paths:</p>

<pre>
df = pd.read_csv("D:/Flor/SaudiArabia/YamnetResults/weather_labels_summaryWithConfidence.csv")
final_sample.to_csv("D:/Flor/SaudiArabia/YamnetResults/sampled_files_Final.csv")
output_folder = "D:/Flor/SaudiArabia/YamnetResults/forvalidation_Final"
html_file = "D:/Flor/SaudiArabia/YamnetResults/validation_page_final.html"
</pre>

<p>Inside the HTML export section, update:</p>

<pre>
a.download = "D:/Flor/SaudiArabia/YamnetResults/validation_resultsFinal.csv";
a.download = "D:/Flor/SaudiArabia/YamnetResults/validation_page_with_editsFinal.html";
</pre>

<h3>Step 3 — Run the Audacity Server</h3>
<p>
To enable the “Open in Audacity” button in the HTML interface, run <code>AudacityServer.py</code> before opening the HTML file.  
Update the script to point to your Audacity installation directory.
</p>

<p>
Once running, open the generated HTML file. You will see an interface that allows you to:
</p>

<ul>
  <li>Listen to each sampled recording</li>
  <li>Open it directly in Audacity</li>
  <li>Assign a validation class</li>
  <li>Write notes</li>
  <li>Export your validation results</li>
</ul>

<hr>


<img width="1665" height="384" alt="image" src="https://github.com/user-attachments/assets/21d7eade-6601-43f8-9de5-ef3443e1e613" />

