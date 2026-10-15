[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.on007473-blue)](https://doi.org/10.82901/nemar.on007473)

This dataset consists of 5 participants completing functional localizer and movie viewing tasks. These data are stored in SNIRF format with optode and landmark locations associated with subject specific head models. 


See the corresponding publication for more information about this dataset:

Tripathy K, Fogarty M, et al., "Mapping brain function in adults and young children during naturalistic viewing with high-density diffuse optical tomography." Human Brain Mapping. 2024 May;45(7):e26684. doi: 10.1002/hbm.26684. PMID: 38703090; PMCID: PMC11069306.

Kalyan Tripathy, Zachary E. Markow, Morgan Fogarty, Mariel L. Schroeder, Alexa M. Svoboda, Adam T. Eggebrecht, Bradley L. Schlaggar, Jason W. Trobaugh, Joseph P. Culver, "Multisensory naturalistic decoding with high-density diffuse optical tomography," Neurophoton. 12(1) 015002 (23 January 2025) https://doi.org/10.1117/1.NPh.12.1.015002

## Stimuli (added 2026-10-08, metadata only)

The movie clips are not included (commercial films and TV episodes). `task-MOVnnn` is a run index within a session, not
a movie identity (the same label shows different clips in different sessions).

- `stimuli/stimuli.tsv`: the 20 clips used in the movie runs (authors' clip names: Finding Nemo `FN_gates_1-4`, Frozen
  `Frozen1-4`, Moana `Moana1-4`, Curious George `CG_D1/D2/SM1/SM2`, Daniel Tiger's Neighborhood `DT1-4`), the source
  work, the movie-period duration in the runs, and where the clip starts in the source. Each start was found by
  correlating the authors' 1-s luminance and auditory-envelope regressors
  (https://github.com/mefogarty/feature-mapping-tutorial, `FeatureRegressors/`) with a copy of the source; for the four
  films the start is the position in one copy and other editions may be offset by a few seconds; for Curious George and
  Daniel Tiger it is the position in the official channel upload listed.
- `stimuli/run_to_clip.tsv`: run -> clip for the 80 movie runs listed in the authors' table `MovieParticipants_Adults.mat`
  (same repository). Every clip has a distinct movie-period duration (0.1-s resolution), which identifies the clip of the
  remaining movie runs.

Known file issues (unchanged here): `*_events.tsv` give `onset` and `duration` in samples (10.42 Hz), not seconds; and
`mne.io.read_raw_snirf` fails on these SNIRF files because `landmarkLabels` is stored 2-D.

### Runs of A04 in ses-7 and ses-8 (added 2026-10-09)

Sub-A04 has 16 movie-task runs outside the 40 A04 movie runs of the 2024 paper (its Supplemental Table ST1 counts
40 movie runs for A04; the authors' run table `MovieParticipants_Adults.mat` covers ses-2 to ses-6): ses-7 MOV002-MOV009 and
ses-8 MOV001-MOV008. The 2025 paper (Tripathy et al., Neurophotonics 12(1):015002, cited above) says that this data set
"was expanded to include additional movie viewing runs" and that supplemental data "were collected from one participant who
listened to audio clips without visuals and watched silent movies stripped of audio for a control experiment"; its
Supplementary Fig. 4A/C: "Participant A04 was presented with four different audio clips without any visuals twice each
over the course of an imaging session" and "with four different silent movie clips twice each over the course of an
imaging session". Two sessions of 8 control runs each match ses-7 and ses-8 (8 runs each) of A04. Which session is the
audio-only one and which the silent-video one, which four clips were used and in what order are not stated, and the SNIRF
sidecars of these runs give only `TaskName` MOVnnn. Until the authors confirm, these 16 runs should not be taken as
audiovisual movie viewing; `stimuli/run_to_clip.tsv` does not list them.
