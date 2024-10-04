---
show: true
width: 12
date: 2024-01-9 00:01:00 +0800
---

<div class="p-4">
    <h2 style="text-align: center; margin-bottom: 20px;">  Seeg-nificant </h2>
    <h3 style="text-align: center; margin-bottom: 20px;">Neural Decoding from stereotactic EEG: accounting for electrode variability across subjects</h3>
    <div style="width: 85%; margin: 0 auto; text-align: center; font-weight: bold; margin-bottom: 20px; font-size: 20px;">
        <span style="margin-right: 20px;">Georgios Mentzelopoulos<sup>1</sup></span>
        <span style="margin-right: 20px;">Evangelos Chatzipantazis<sup>1</sup></span>
        <span style="margin-right: 20px;">Ashwin Ramayya<sup>2</sup></span>
        <span style="margin-right: 20px;">Michelle J. Hedlund<sup>2</sup></span>
        <span style="margin-right: 20px;">Vivek P. Buch<sup>2</sup></span>
        <span style="margin-right: 20px;">Kostas Daniilidis<sup>1</sup></span>
        <span style="margin-right: 20px;">Konrad P. Kording<sup>1</sup></span>
        <span style="margin-right: 20px;">Flavia Vitale<sup>1</sup></span>
    </div>
    <p style="text-align: center; margin-bottom: 20px; font-size: 18px;">
        <sup>1</sup>
        <img src="{{ 'assets/images/badges/upenn_logo.jpg' | relative_url }}" alt="Penn Logo" style="width: 40px; height: auto; vertical-align: middle;">
        <span style="margin-right: 20px;"> University of Pennsylvania </span>
        <sup>2</sup>
        <img src="{{ 'assets/images/badges/stanford.png' | relative_url }}" alt="Stanford Logo" style="width: 27px; height: auto; vertical-align: middle;">
        <span style="margin-right: 20px;"> Stanford University </span>
    <!-- New line for Arxiv and GitHub logos with "Coming soon" tooltips -->
    <p style="text-align: center; margin-bottom: 20px;">
        <img src="{{ 'assets/images/badges/arxiv.jpg' | relative_url }}" alt="Arxiv Logo" title="Paper coming soon" style="width: 30px; height: auto; vertical-align: middle; margin-right: 0px; cursor: not-allowed;">
        Paper
        <img src="{{ 'assets/images/badges/github.png' | relative_url }}" alt="GitHub Logo" title="Code coming soon" style="width: 30px; height: auto; vertical-align: middle; margin-right: 5px; margin-left: 40px;cursor: not-allowed;">
        Code
    </p>
    <h5 style="margin-top: 30px">Abstract</h5> 
    <hr />
    <p style="text-align: justify; margin-bottom: 20px">
    Deep learning based neural decoding from stereotactic electroencephalography (sEEG) would likely benefit from scaling
    up both dataset and model size. To achieve this, combining data across multiple subjects is crucial. However, in 
    sEEG cohorts, each subject has a variable number of electrodes placed at distinct locations in their brain, solely 
    based on clinical needs. Such heterogeneity in electrode number/placement poses a significant challenge for data 
    integration, since there is no clear correspondence of the neural activity recorded at distinct sites between 
    individuals. 
    </p>
    <p style="text-align: justify; margin-bottom: 20px">
    Here we introduce a training framework and architecture that can be used to decode behavior across
    subjects using sEEG data. We tokenize the neural activity within electrodes using convolutions and extract 
    long-term temporal dependencies between tokens using self-attention in the time dimension. The 3D location of each 
    electrode is then mixed with the tokens, followed by another self-attention in the electrode dimension to extract
    effective spatiotemporal neural representations. Subject-specific heads are then used for downstream decoding tasks.
    Using this approach, we construct a multi-subject model trained on the combined data from 21 subjects performing 
    a behavioral task. 
    </p>
    <p style="text-align: justify; margin-bottom: 20px">
    We demonstrate that our model is able to decode the trial-wise response time of the subjects 
    during the behavioral task solely from neural data. We also show that the neural representations learned by 
    pretraining our model across individuals can be transferred in a few-shot manner to new subjects. This work 
    introduces a scalable approach towards sEEG data integration for multi-subject model training, paving the way for
    cross-subject generalization for sEEG decoding.  
    </p>
    <h5 style="margin-top: 30px">Dataset & Challenges</h5> 
    <hr />
    <p style="text-align: justify;">
    <strong> Dataset. </strong> We collected a dataset of 23 subjects that were implanted with sEEG electrodes as part of
    their medical care. The subjects in our dataset where mixed in terms of sex (8 male, 13 female) and age (ranging 
    from 16-57 years old). Each subject was implanted with a variable number of electrodes at district locations in
    their brain, solely based on clinical needs. Across subjects electrodes span white and grey matter; cortical,
    subcortical, and deep structures.
    </p>
    <p>
    <strong> Behavioral Task. </strong> While implated  with sEEG, study participants performed a repetitive, reaction
    time task. In each trial, a visual stimulus was presented. After a variable delay, the stimulus changed color. 
    At that time, the participant responded by pressing a button as fast as they could. 
    </p>
    <p>
    <strong> Problem. </strong> Our goal was to decode the trial-wise response time of the participants using their 
    sEEG.
    </p>
    <!-- Figure with Caption -->
    <!-- Centered Figure with Limited Width -->
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/electrode_placement.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 100%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px;">
        Figure 1. <strong> Dataset & Behavioral Experiment. </strong> <strong>(A)</strong> Electrode Placement for 4 example subjects 
        in our cohort, <strong>(B)</strong> All electrodes of all subject in our cohort projected onto a unified brain template,
        <strong>(C)</strong> Schematic of the behavioral task that subjects completed.
        </figcaption>
    </div>
</div>


