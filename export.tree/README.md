# SemReps-8K attention modulation and imagery

This dataset is an extension to the [SemReps-8K dataset](https://openneuro.org/datasets/ds007272/). It contains fMRI recordings of 5 subjects viewing stimuli in the form of images of naturalistic scenes and captions of such images with a modulation of attention: The subjects are attending either to the images or to the captions. The stimuli are the same 140 stimuli used for the test data of [SemReps-8K](https://openneuro.org/datasets/ds007272/)

The dataset also includes additional trials during which the subjects were performing mental imagery of 50 different visual scenes.

## Experiment details

Five subjects (2 female and 3 male, age between 22 and 47 years, all right-handed and fluent English speakers) participated in the experiment after providing informed consent.
All five subjects also participated in a previous experiment during which they were viewing images and reading captions without any modulation of attention. More details on data collection and preprocessing of this first experiment can be found in the [original SemReps-8K paper](https://elifesciences.org/reviewed-preprints/107933). The data from this experiment is used as training data for the decoders, and the additionally recorded data described in the following is used only as test data.
The study was performed in accordance with French national ethical regulations (Comité de Protection des Personnes, ID 2019-A01920-57). 
We collected functional MRI data using a 3T Philips ACHIEVA scanner (gradient echo pulse sequence, TR=2s, TE=30ms, 46 slices with a 32-channel head coil, slice thickness=3mm with 0.2mm gap, in-plane voxel dimensions 3×3mm). At the start of each session, we further acquired high-resolution anatomical images for each subject (voxel size=1mm$^3$, TR=8.13ms, TE=3.74ms, 170 sagittal slices).

Scanning was spanned over 8 sessions (except for sub-04: 9 sessions), each consisting of 15 runs during which the subjects were presented with 48 stimuli. Before and after the perception trials there were 4 imagery trials. At the start and end of each run there was an 8s fixation period.

### Attention modulation conditions

The stimulus type varied randomly inside each run between images and captions. Each stimulus was presented for 2.5 seconds at the center of the screen (visual angle: 14.6 degrees; captions were displayed in white on a dark gray background (font: ``Consolas''). The inter-stimulus interval was 1s. 7 fixation trials of 2.5s were randomly occurring during the presentation of stimuli.

Subjects performed a one-back matching task: They were instructed to press a button whenever the stimulus matched the immediately preceding one.
However, in this experiment the participants were instructed to either only pay attention to only one of the modalities (images or captions) for this task. More specifically, at the start of each run there was an instruction to either attend to the images or captions, meaning that the button should be pressed if there was a repetition of two stimuli in the target modality (even if multiple non-target stimuli occurred in between). The stimuli from the non-target modality could completely be ignored for the task. During half of the runs the participants had to attend to images, during the other half to captions. 

Images and captions were taken from the COCO dataset ([COCO - Common Objects in Context](https://cocodataset.org/#home)). We used the same 140 stimuli (70 images and 70 matching captions) as used for the test set of [SemReps-8K](https://elifesciences.org/reviewed-preprints/107933). 

These stimuli were presented repeatedly to each subject in order to reduce noise (on average: 20 times).

### Imagery conditions

Each imagery trial consisted of the presentation of the caption serving as imagery instruction (3s), a 1s fixation period, and 10s presentation of a light gray box on the screen during which the participants should imagine a scene matching the preceding caption. Finally, there was a 2s fixation period.

In total, there were 50 different captions that served as imagery instructions. These 50 captions were the same for all subjects. Each caption was repeated on average 20 times to obtain a higher signal-to-noise ratio.

## Data structure

Data is organized according to [BIDS](http://bids.neuroimaging.io/).

Functional and anatomical scans can be found in the respective folders named according to the subject identifiers (e.g. sub-01). All anatomical scans were anonymized using [pydeface](https://github.com/poldracklab/pydeface).

The `derivatives/betas` directory contains preprocessed `betas` for each training, test and imagery stimulus for each subject in their respective subject-specific space (volume). For details on how these were extracted please refer to the paper. In `derivatives/betas/surface` we additionally provide surface-projections onto fsaverage of these betas.

## Citation

If you make use of the SemReps-8K dataset, please cite the corresponding paper:

Nikolaus, M., Mozafari, M., Berry, I., Asher, N., Reddy, L., & VanRullen, R. (2025). Modality-Agnostic Decoding of Vision and Language from fMRI. eLife.
https://doi.org/10.7554/eLife.107933

If you make use of the attention modulation conditions of the SemReps-8K dataset, please cite the corresponding paper:

Nikolaus, M., Mozafari, M., Berry, I., Reddy, L., & VanRullen, R. (2026). Attention Increases the Spread of Modality-Invariant Information across the Cortex. Imaging Neuroscience.

If you make use of the imagery conditions of the SemReps-8K dataset, please cite the corresponding paper:

Nikolaus, M., Mozafari, M., Berry, I., Reddy, L., & VanRullen, R. (2026). Leveraging modality-agnostic decoders for decoding of mental imagery. Under review at eNeuro.

## Acknowledgements

This research was funded by grants from the French Agence Nationale de la Recherche (ANR: AI-REPS grant number ANR-18-CE37-0007-01 and ANITI grant number ANR-19-PI3A-0004) as well as the European Union (ERC Advanced grant GLoW, 101096017). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.

We thank the Inserm/UPS UMR1214 Technical Platform for their help in setting up and for the acquisitions of the MRI sequences.
