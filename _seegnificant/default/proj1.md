---
show: true
width: 12
date: 2024-01-9 00:01:00 +0800
---

<div class="p-4">
    <!-- <h2 style="text-align: center; margin-bottom: 20px;">  Seeg-nificant </h2> -->
    <h3 style="text-align: center; margin-bottom: 20px;">Neural decoding from stereotactic EEG: accounting for electrode variability across subjects</h3>
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
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    Deep learning based neural decoding from stereotactic electroencephalography (sEEG) would likely benefit from scaling
    up both dataset and model size. To achieve this, combining data across multiple subjects is crucial. However, in 
    sEEG cohorts, each subject has a variable number of electrodes placed at distinct locations in their brain, solely 
    based on clinical needs. Such heterogeneity in electrode number/placement poses a significant challenge for data 
    integration, since there is no clear correspondence of the neural activity recorded at distinct sites between 
    individuals. 
    </p>
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    Here we introduce a training framework and architecture that can be used to decode behavior across
    subjects using sEEG data. We tokenize the neural activity within electrodes using convolutions and extract 
    long-term temporal dependencies between tokens using self-attention in the time dimension. The 3D location of each 
    electrode is then mixed with the tokens, followed by another self-attention in the electrode dimension to extract
    effective spatiotemporal neural representations. Subject-specific heads are then used for downstream decoding tasks.
    Using this approach, we construct a multi-subject model trained on the combined data from 21 subjects performing 
    a behavioral task. 
    </p>
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    We demonstrate that our model is able to decode the trial-wise response time of the subjects 
    during the behavioral task solely from neural data. We also show that the neural representations learned by 
    pretraining our model across individuals can be transferred in a few-shot manner to new subjects. This work 
    introduces a scalable approach towards sEEG data integration for multi-subject model training, paving the way for
    cross-subject generalization for sEEG decoding.  
    </p>
    <h5 style="margin-top: 30px">Dataset</h5> 
    <hr />
    <p style="text-align: justify; font-size: 17px">
    <strong> Dataset. </strong> We collected a dataset of 23 subjects that were implanted with sEEG electrodes as part of
    their medical care. The subjects in our dataset where mixed in terms of sex (8 male, 13 female) and age (ranging 
    from 16-57 years old). Each subject was implanted with a variable number of electrodes at district locations in
    their brain, solely based on clinical needs. Across subjects electrodes span white and grey matter; cortical,
    subcortical, and deep structures. 
    </p>
    <p style="; font-size: 17px">
    <strong> Behavioral Task. </strong> While implated  with sEEG, study participants performed a repetitive, reaction
    time task. In each trial, a visual stimulus was presented. After a variable delay, the stimulus changed color. 
    At that time, the participant responded by pressing a button as fast as they could. 
    </p>
    <!-- Figure with Caption -->
    <!-- Centered Figure with Limited Width -->
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/electrode_placement.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 80%; height: auto;">
        <figcaption style="text-align: center; font-size: 17px; margin-top: 5px;">
        Figure 1. <strong> Dataset & Behavioral Experiment. </strong> <strong>(A)</strong> Electrode Placement for 4 example subjects 
        in our cohort, <strong>(B)</strong> All electrodes of all subject in our cohort projected onto a unified brain template,
        <strong>(C)</strong> Schematic of the behavioral task that subjects completed.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px">Objective & Challenges</h5>
    <hr />
    <p style="; font-size: 17px">
    <strong> Objective. </strong> Decode the trial-wise response time of the participants using their sEEG.
    </p>
    <p style="margin-top: 20px; margin-bottom: 10px ;font-size: 17px"> <strong>Challenges. </strong> </p>
    <ul style="; font-size: 17px">
      <li><strong>Variability of electrode number across subjects: </strong> Subjects in our cohort where monitored with
        sEEG electrodes as part of their medical care. Therefore, the number of electrodes that each subject was 
        implanted was based on the subject's clinical needs. The number of electrodes varied from tens to hundreds 
        across subjects. </li>
      <li><strong>Variability of electrode placement across subjects: </strong> While the brain region in which electrodes are
        implanted in each subject is known, the identity of the neural population monitored by each electrode, or what
        stimuli that population responds to is unknown. </li>
      <li><strong>Limited amount of data for each subject:</strong> Subjects voluntarily 
        participated in our study while staying in the epilepsy monitoring unit, where they received medical care. 
        Therefore, the amount of time they can devode is very limited. In our study, each subject performed 
        &sim; 175 trials of the behavioral task.</li>
        <li><strong>Variability in behavioral outcomes across subjects:</strong> Each subject's response times across 
        trials had a unique statistical profile, with the mean and variance of response times varying across subjects. </li>
    </ul>
    <h5 style="margin-top: 30px"> Signal Processing </h5> 
    <hr />
    <p style="; font-size: 17px">
        Motivated by the lack of correspondence between the neural activity recorded
        between subjects, we sought to identify the subset of electrodes across subjects that respond to stimulus 
        color-change during the behavioral task. We identified those electrodes using methods developed by 
        Paraskevopoulou et al. (2021) using each electrode's high-gamma power. This procedure isolated electrodes that
        monitor neural populations that are relevant to the task, and therefore are likely to contain information about 
        the response time of the subject for each trial. The electrical activity of those electrodes was then used for
        response time decoding.
    </p>
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/responsive_electrodes.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 60%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; font-size: 17px">
        Figure 2. <strong> Neural activation patterns during task for an example subject. </strong> Each dot on the 
        brain template represents an electrode that either responds to the stimulur color-change (cyan) or not (gray). 
        Each panel shows the high-gamma timecourse of all trials for 1.5 sec after the stimulus color-change. Black 
        dots within panels show the subject's response time for each trial.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Network Architecture </h5> 
    <hr />
    <p style="margin-top: 30px; font-size: 17px">
    Having identified electrodes whose neural activity patterns contain 
    information about the response times for each trial, our problem now reduces to building a map from the multivariate/
    timeseries of neural activity of each trial, to the response time of the same trial. 
    </p>
    <p style="margin-top: 30px; font-size: 17px">
    To build this map, we use the following building blocks:
    <ul style="; font-size: 17px">
    <li>
    <strong> Tokenization: </strong> To tokenize the neural activity, we perform convolutions for each 
    electrode separately. 
    </li>   
    <li>
    <strong> Attention in time: </strong> Having tokenized the neural activity, we process the tokens with 
    self-attention in the time dimension, to capture long term dependencies within the tokens.
    </li>
    <li>
    <strong> Spatial Positional Encoding: </strong> Using each electrodes MNI coordinates, we mix the tokens with information
    about their location in the brain.
    </li>
    <li>
    <strong> Attention in space: </strong> We then process the tokens with another self-attention in the space 
    dimension, to capture long-range dependencies of the neural activity across electrodes.
    </li>
    <li>
    <strong> Compression: </strong> The latents are then unrolled and projected to a lower dimensional 
    representation using a multi-layer perceptron.
    </li>
    <li>
    <strong> Subject specific regression heads: </strong> The latents are then projected to a single 
    value, which represents the response time of a given trial, using MLPs that are unique for each subject. A
    different MLP is assigned for each subject since the response time profile of each subject is unique.
    </li>
    </ul>
    </p>
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/architecture.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 80%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; font-size: 17px">
        Figure 3. <strong> Outline of our network architecture </strong>. The sEEG signals are converted to vector 
        embeddings through temporal convolutions and then processed by sequential self-attention operations in the time 
        and electrode dimensions in an alternating fashion. The latents are compressed and projected through 
        subject-specific task heads to obtain behavioral predictions.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Training Single- and Multi-subject Models </h5> 
    <hr />
    <p style="text-align: justify; font-size: 17px">
    <strong> Training single subject models. </strong> To test whether our modeling approach would be able to decode 
    the trial-wise response time from sEEG data, we began with a within-subject approach, where we trained a separate model for each 
    subject. <strong>Across the 21 single-subject models, the average test set $R^2$ was 0.30 &plusmn;  0.05 (mean &plusmn;  sem) </strong>
    </p>
    <p style="text-align: justify; font-size: 17px">
    <strong> Training a multi-session, multi-subject model. </strong> To investigate whether training on more data, 
    would improve decoding performance, we trained a unified, multi-subject model on the combined data of all subjects.
    <strong>Across subjects, the average per-subject test set $R^2$ was 0.39 $\pm$ 0.05 (mean $\pm$ sem). </strong> 
    The multi-subject training approach boosted decoding performance by $\Delta R^{2}$ = 0.09, on average, compared to
    training on single subjects.
    </p>
    <p style="text-align: justify; font-size: 17px">
    <strong> Finetuning the multi-session, multi-subject model to single subjects. </strong> We then tested whether 
    finetuning the multi-subject model to individual subjects would further boost the performance gains.
    <strong> The multi-seubject model, finetuned to each subject achieved an average per0subject test set
    $R^2$ score of 0.41 $\pm$ 0.05 </strong>. Finetuning the multi-subject model to individual subjects boosted the\
    performance gains by $\Delta R^{2}$ = 0.11, on average, compared to single subject models.
    </p>
    <div style="text-align: center; margin-top: 30px">
        <img src="{{ 'assets/images/etc/ms_vs_ss.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 3. <strong> Comparing decoding performance between the single-subject and multi-subject models for
        each subject. </strong> <strong> A </strong>. Single-subject vs multi-subject model. <strong> B </strong>. 
        Single-subject vs finetuned, multi-subject model. 
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Transferring multi-subject models to new subjects </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 30px; font-size: 17px">
    <strong> Transferring the multi-session, multi-subject model to new subjects. </strong> 
    We were interested in identifying whether the representations learned by pretraining our models on multiple 
    subjects can efficiently be transferred to new subjects, unseen from the model during training. This is important
    in any real-world clinical scenario, where only a few number of behavioral trials can be collected from a subject.
    To test this, we employed a leave-one-out cross validation approach. We trained 21 models, each of which was
    trained on the combined data of all subjects but one. The weights of the pretrained models were then used as
    the basis for finetuning on the data of each left-out participant, unseen from the models during training.
    <strong> Across subjects, the  models trained on other subjects and finetuned to a new one achieved an average test set
    $R^{2}$ of 0.38 $\pm$ 0.05 (mean $\pm$ sem). </strong> The finetuned single-subject models showed a
    decoding performance increase $\Delta R^{2}$ = 0.08 compared to the single-subject models trained from scratch.
    </p>
    <div style="text-align: center; margin-top: 20px">
        <img src="{{ 'assets/images/etc/ss_ssf.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 3. <strong> Comparing decoding performance between </strong> <strong> (A) </strong> Transferred 
        single-subject finetuned models vs  single-subject models trained from scratch, and <strong> (B) </strong> 
        Transferred single-subject finetuned models vs the multi-session, multi-subject model.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Baseline comparisons </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 20px; font-size: 17px">
    To ensure that our model's decoding performance is worth the computational burden, we compared our models against
    various baselines. Our proposed architecture outperformed all baseline models when trained on either single subjects
    or across all subjects. 
    <div style="text-align: center; margin-top: 20px">
        <img src="{{ 'assets/images/etc/baseline_comparisons.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 3. <strong> Decoding performance (mean $\pm$ sem) for various baselines and our proposed models. </strong>
        </figcaption>
    </div>
    </p>
    <h5 style="margin-top: 30px"> Citation </h5> 
    <hr />
    <!-- Citation Section -->
    <div style="border: 1px solid #ddd; padding: 15px; background-color: #f9f9f9; margin: 20px auto; width: 100%; text-align: left; font-family: monospace; line-height: 1.5;">
    <div class="citation">
    <pre><code>@inproceedings{
    mentzelopoulos2024,
    title={Neural Decoding from stereotactic EEG: accounting for electrode variability across subjects},
    author={Georgios Mentzelopoulos and Evangelos Chatzipantazis and Ashwin Ramayya and Michelle J. Hedlund and Vivek P. Buch and Kostas Daniilidis and Konrad P. Kording and Flavia Vitale},
    booktitle={Thirty-eighth Conference on Neural Information Processing Systems},
    year={2024},
    }</code></pre>
    </div>
    </div>
<!--/div-->


