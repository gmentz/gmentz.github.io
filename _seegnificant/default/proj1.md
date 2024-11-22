---
show: true
width: 12
date: 2024-01-9 00:01:00 +0800
---

<div class="p-4">
    <!-- <h2 style="text-align: center; margin-bottom: 20px;">  Seeg-nificant </h2> -->
    <h3 style="text-align: center; margin-bottom: 20px;">Neural decoding from stereotactic EEG: accounting for electrode variability across subjects</h3>
    <div style="width: 90%; margin: 0 auto; text-align: center; margin-bottom: 20px; font-size: 20px;">
        <span style="margin-right: 20px;">Georgios Mentzelopoulos<sup>1</sup></span>
        <span style="margin-right: 20px;">Evangelos Chatzipantazis<sup>1</sup></span>
        <span style="margin-right: 20px;">Ashwin G. Ramayya<sup>2</sup></span>
        <span style="margin-right: 20px;">Michelle J. Hedlund<sup>2</sup></span>
        <span style="margin-right: 20px;">Vivek P. Buch<sup>2</sup></span>
        <span style="margin-right: 20px;">Kostas Daniilidis<sup>1, 3</sup></span>
        <span style="margin-right: 20px;">Konrad P. Kording<sup>1</sup></span>
        <span style="margin-right: 20px;">Flavia Vitale<sup>1</sup></span>
    </div>
    <p style="text-align: center; margin-bottom: 20px; font-size: 18px;">
        <sup>1</sup> <span style="margin-right: 2px;"> University of Pennsylvania </span>
        <img src="{{ 'assets/images/badges/penn_logo_2.png' | relative_url }}" alt="Penn Logo" style="width: 50px; height: auto; vertical-align: middle; margin-right: 15px">
        <!-- <span style="margin-right: 20px;"> University of Pennsylvania </span> -->
        <sup>2</sup> <span style="margin-right: 2px;"> Stanford University </span>
        <img src="{{ 'assets/images/badges/stanford.png' | relative_url }}" alt="Stanford Logo" style="width: 25px; height: auto; vertical-align: middle; margin-right: 15px">
        <!-- <span style="margin-right: 20px;"> Stanford University </span> -->
        <sup>3</sup> <span style="margin-right: 2px;"> Archimedes, Athena RC </span>
        <img src="{{ 'assets/images/badges/archimedes_logo.png' | relative_url }}" alt="Archimedes Logo" style="width: 29px; height: auto; vertical-align: middle;">
        <!-- <span style="margin-right: 20px;"> Archimedes, Athena RC </span> -->
    <!-- New line for Arxiv and GitHub logos with "Coming soon" tooltips -->
    <p style="text-align: center; margin-bottom: 20px;">
        <a href="https://openreview.net/pdf?id=LR1nnsD7H0"  target="_blank" title="Link to Open Review" style="text-decoration: none;">
        <img src="{{ 'assets/images/badges/paper.jpg' | relative_url }}" alt="Arxiv Logo" title="Link to Open Review" style="width: 16px; height: auto; vertical-align: top; margin-right: 5px;">
        Paper
        </a>
        <a href="https://github.com/gmentz/seegnificant"  target="_blank" title="Link to Codebase" style="text-decoration: none;">
            <img src="{{ 'assets/images/badges/github.png' | relative_url }}" alt="GitHub Logo" style="width: 23px; height: auto; vertical-align: top; margin-right: 5px; margin-left: 40px;">
            Code
        </a>
    </p>
    <p style="text-align: center; margin-bottom: 20px;"> Published at the 38th Conference on Neural Information Processing Systems
    <a href="https://neurips.cc/Conferences/2024" target="_blank"> (NeurIPS 2024).</a> <p>
    <h5 style="margin-top: 30px">Abstract</h5> 
    <hr />
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    Deep learning based neural decoding from stereotactic electroencephalography (sEEG) would likely benefit from
    scaling up both dataset and model size. To achieve this, combining data across multiple subjects is crucial. 
    However, in sEEG cohorts, each subject has a variable number of electrodes placed at distinct locations in their 
    brain, solely based on clinical needs. Such heterogeneity in electrode number/placement poses a significant 
    challenge for data integration, since there is no clear correspondence of the neural activity recorded at distinct
    sites between individuals.
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    <strong><i>Here we introduce seegnificant: a training framework and architecture that can be used
    to decode behavior across subjects using sEEG data</i></strong>. We tokenize the neural activity within electrodes using
    convolutions and extract long-term temporal dependencies between tokens using self-attention in the time dimension. 
    The 3D location of each electrode is then mixed with the tokens, followed by another self-attention in the
    electrode dimension to extract effective spatiotemporal neural representations. Subject-specific heads are then
    used for downstream decoding tasks.
    </p>
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    Using this approach, we construct a multi-subject model trained on the combined
    data from 21 subjects performing a behavioral task. We demonstrate that our model is able to decode the trial-wise
    response time of the subjects during the behavioral task solely from neural data. We also show that the neural
    representations learned by pretraining our model across individuals can be transferred in a few-shot manner to
    new subjects. This work introduces a scalable approach towards sEEG data integration for multi-subject model
    training, paving the way for cross-subject generalization for sEEG decoding.
    </p>
    <h5 style="margin-top: 30px">Dataset</h5> 
    <hr />
    <p style="text-align: justify; font-size: 17px">
    <strong> Neural Recordings. </strong> We obtained neural recordings from 21 subjects that were implanted with sEEG electrodes as part of
    their medical care for medical refractory epilepsy. Based on clinical needs alone, each subject was implanted with a variable number of electrodes at district locations in
    their brain (see Fig. 1). Subjects were mixed in terms of sex (8 male, 13 female), age (ranging from 16-57 years old), and ethnic background. 
    </p>
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/dataset_seeg.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 100%; height: auto;">
        <figcaption style="text-align: center; font-size: 17px; margin-top: 5px;">
        Figure 1. <strong> Electrode placement for each subject in our cohort projected on an MNI brain template. </strong> Grey dots show behaviorally relevant electrodes, 
        while grey dots represent behaviorally irrelevant electrodes (see Signal Processing).
        </figcaption>
    </div>
    <p style="; font-size: 17px; margin-top: 15px">
    <strong> Behavioral Task. </strong> Subjects completed the color-change detection task (a repetitive, reaction
    time task) while their sEEG was simultaneously recorded (see Fig. 2). In each trial of the task, a visual stimulus was presented. After a variable delay, the stimulus changed color. 
    At that time, the subject responded by pressing a button as fast as they could.
    </p>
    <!-- Figure with Caption -->
    <!-- Centered Figure with Limited Width -->
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/behavioral_task.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 50%; height: auto;">
        <figcaption style="text-align: center; font-size: 17px; margin-top: 5px;">
        Figure 2. <strong> Schematic of the behavioral task completed by subjects. </strong> 
        </figcaption>
    </div>
    <h5 style="margin-top: 30px">Mission</h5>
    <hr />
    <p style="; font-size: 17px">
    <strong> <i>Our goal was to build a multi-subject model capable of decoding the trial-wise response time of subject using their sEEG. </i></strong> 
    </p>
    <p style="margin-top: 20px; margin-bottom: 10px ;font-size: 17px"> <strong>Challenges. </strong> </p>
    <ul style="; font-size: 17px">
      <li><strong>Variability of electrode number/placement across subjects: </strong> Subjects were implanted with
        sEEG as part of their medical care, so the number and placement of electrodes was determined solely based on
        clinical needs. Therefore, there is no clear correspondence between the neural activity recorded 
        between individuals.  
        </li>
      <li><strong>Limited amount of per-subject data:</strong> Due to clinical circumstances, each subject completed 
        only a few behavioral trials ($\sim$ 175 trials per subject). This is a barrier to scaling up, since neural networks require a lot of data
        to generalize effectively. </li>
      <li><strong>Variability in behavioral outcomes across subjects:</strong> The response time statistics 
        of each subject are unique (how fast they respond on average), posing a significant challenge
        to integrating data across subjects.</li>
    </ul>
    <h5 style="margin-top: 30px"> Signal processing </h5> 
    <hr />
    <p style="; font-size: 17px">
        Motivated by the lack of correspondence between the neural activity recorded
        across subjects, we sought to identify  the subset of electrodes that respond to the stimulus 
        color-change during the behavioral task. We identified those electrodes using methods developed by 
        <a href="http://dx.doi.org/10.1016/j.neuroimage.2021.118127" target="_blank"> 
        Paraskevopoulou et al. (2021)</a> based on each electrode's high-gamma power (narrowband neural activity with
        frequency content between 70-150 Hz). This procedure isolated electrodes that
        monitor neural populations that are relevant to the task, and therefore are likely to contain information about 
        the response time of the subject for each trial (Fig. 3). The electrical activity of those electrodes was then used for
        response time decoding.
    </p>
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/responsive_electrodes.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 70%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; font-size: 17px">
        Figure 3. <strong> Neural activity for behaviorally relevant electrodes during task for an example subject. </strong> Each dot on the 
        brain template shows an electrode that either responds to the stimulus color-change (cyan) or not (gray). 
        Each panel shows the high-gamma timecourse of an electrode, of all trials, for 1.5 sec after the stimulus color-change. Black 
        dots within panels show the subject's response time for each trial.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Network architecture </h5> 
    <hr />
    <p style="margin-top: 30px; font-size: 17px">
    Having identified electrodes whose neural activity contains 
    information about each trial's response time, our problem reduced to building a map from the multivariate
    timeseries of neural activity of each trial to the response time of the same trial. 
    </p>
    <p style="margin-top: 30px; font-size: 17px">
    We built this map using the network show in Fig. 4, composed of the following building blocks:
    <ul style="; font-size: 17px">
    <li>
    <strong> Temporal CNN (Tokenizer): </strong> We use a CNN that operates on each electrode separately to tokenize the neural 
    activity of each electrode.
    </li>   
    <li>
    <strong> Self-attention in time: </strong> Having tokenized the neural activity, we process the tokens with 
    self-attention <a href="https://doi.org/10.48550/arXiv.1706.03762" target="_blank"> 
    [Vaswani et al. (2017)] </a> in the time dimension, to capture long-term dependencies between timepoints.
    </li>
    <li>
    <strong> Spatial positional encoding: </strong> Using MNI coordinates, we add information about each
    electrode's location in the brain to the tokens.
    </li>
    <li>
    <strong> Self-attention in space: </strong> We then process the tokens with another self-attention 
    <a href="https://doi.org/10.48550/arXiv.1706.03762" target="_blank"> [Vaswani et al. (2017)] </a> in the electrode 
    dimension, to capture long-range dependencies of the neural activity across electrodes.
    </li>
    <li>
    <strong> Compression: </strong> The tokens are then projected to a lower dimensional 
    representation using an MLP.
    </li>
    <li>
    <strong> Subject specific regression heads: </strong> The representations are then projected to a single 
    value, which is the response time estimate of a given trial, using MLPs that are unique for each subject. 
    </li>
    </ul>
    </p>
    <div style="text-align: center;">
        <figure style="display: inline-block; margin: 0;">
            <img src="{{ 'assets/images/etc/architecture.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 80%; height: auto;">
            <figcaption style="font-size: 16px; margin-top: 5px; width: 100%; text-align: center;">
                Figure 4. <strong>Network architecture</strong>. 
            </figcaption>
        </figure>
    </div>
    <h5 style="margin-top: 30px"> Results: single- and multi-subject model training </h5> 
    <hr />
    <p style="text-align: justify; font-size: 17px">
    <strong> Training single subject models. </strong> To test whether our modeling approach would be able to decode 
    the trial-wise response time from sEEG data, we first trained a separate model for each 
    subject. <strong>Across the 21 single-subject models, the average test set $R^2$ was 0.30 &plusmn;  0.05 (mean &plusmn;  sem) </strong>
    </p>
    <p style="text-align: justify; font-size: 17px">
    <strong> Training a multi-subject model. </strong> To investigate whether training on more data, despite the 
    heterogeneity, would improve decoding performance, we trained a multi-subject model on the combined data of all subjects.
    <strong>The average per-subject test set $R^2$ for the multi-subject model was 0.39 $\pm$ 0.05 (mean $\pm$ sem). </strong> 
    The multi-subject training approach boosted decoding performance by $\Delta R^{2}$ = 0.09, on average, compared to
    training on single subjects (Fig. 5A).
    </p>
    <p style="text-align: justify; font-size: 17px">
    <strong> Finetuning the multi-subject model to single subjects. </strong> We then tested whether 
    finetuning the multi-subject model to individual subjects would further boost the performance gains.
    <strong> The multi-subject model, finetuned to each subject achieved an average per-subject test set
    $R^2$ score of 0.41 $\pm$ 0.05 </strong>. Finetuning the multi-subject model to individual subjects boosted the
    performance gains by $\Delta R^{2}$ = 0.11, on average, compared to single subject models (Fig. 5B).
    </p>
    <div style="text-align: center; margin-top: 30px">
        <img src="{{ 'assets/images/etc/ms_vs_ss.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 5. <strong> Comparing decoding performance between </strong> <strong> (A) </strong> single-subject vs multi-subject model and <strong> (B) </strong>
        single-subject vs finetuned, multi-subject model. 
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Results: transferring multi-subject models to new subjects </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 30px; font-size: 17px">
    <strong> Transferring the multi-subject model to new subjects. </strong> 
    We were interested in identifying whether the multi-subject models can efficiently be transferred to new subjects, 
    unseen from the model during training. To test this, we employed a leave-one-out cross validation approach. We trained 21 models, each of which was
    trained on the combined data of all subjects but one. The weights of the pretrained models were then used as
    the basis for finetuning on the data of each left-out participant.
    <strong> Across subjects, the  models trained on other subjects and transferred to a new one achieved an average 
    test set $R^{2}$ of 0.38 $\pm$ 0.05 (mean $\pm$ sem). </strong> The transferred single-subject models showed a
    decoding performance increase $\Delta R^{2}$ = 0.08 compared to the single-subject models trained from scratch (Fig. 6A) and 
    showed decoding performance similar to the multi-subject model (Fig. 6B).
    </p>
    <div style="text-align: center; margin-top: 20px">
        <img src="{{ 'assets/images/etc/ss_ssf.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 6. <strong> Comparing decoding performance between </strong> <strong> (A) </strong> transferred 
        single-subject finetuned models vs  single-subject models trained from scratch, and <strong> (B) </strong> 
        transferred single-subject finetuned models vs the multi-subject model.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Results: baseline comparisons </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 20px; font-size: 17px">
    Last, we compared our modeling approach against other traditional and state-of-the art neural decoding approaches.
    <strong> Seegnificant outperformed all other approaches when 
    trained on single subjects, multiple subjects, and when transferred </strong> (Fig. 7).
    <div style="text-align: center; margin-top: 20px">
        <img src="{{ 'assets/images/etc/baseline_comparisons.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 7. <strong> Decoding performance (mean $\pm$ sem) for various baselines and our proposed models. </strong>
        </figcaption>
    </div>
    </p>
    <h5 style="margin-top: 30px"> Citation </h5> 
    <hr />
    <!-- Citation Section -->
    <pre><code>@inproceedings{
    mentzelopoulos2024neural,
    title={Neural decoding from stereotactic EEG: accounting for electrode variability across subjects},
    author={Mentzelopoulos, Georgios and Chatzipantazis, Evangelos and Ramayya, Ashwin G and Hedlund, Michelle and Buch, Vivek and Daniilidis, Kostas and Kording, Konrad and Vitale, Flavia},
    booktitle={The Thirty-eighth Annual Conference on Neural Information Processing Systems}
    }
    </code></pre>
<!--/div-->


