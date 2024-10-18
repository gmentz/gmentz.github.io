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
        <img src="{{ 'assets/images/badges/upenn_logo.jpg' | relative_url }}" alt="Penn Logo" style="width: 30px; height: auto; vertical-align: middle;">
        <span style="margin-right: 20px;"> University of Pennsylvania </span>
        <sup>2</sup>
        <img src="{{ 'assets/images/badges/stanford.png' | relative_url }}" alt="Stanford Logo" style="width: 17px; height: auto; vertical-align: middle;">
        <span style="margin-right: 20px;"> Stanford University </span>
    <!-- New line for Arxiv and GitHub logos with "Coming soon" tooltips -->
    <p style="text-align: center; margin-bottom: 20px;">
        <img src="{{ 'assets/images/badges/arxiv.jpg' | relative_url }}" alt="Arxiv Logo" title="Paper coming soon" style="width: 20px; height: auto; vertical-align: top; margin-right: 0px; cursor: not-allowed;">
        Paper
        <a href="https://github.com/gmentz/seegnificant" title="Link to Codebase" style="text-decoration: none;">
            <img src="{{ 'assets/images/badges/github.png' | relative_url }}" alt="GitHub Logo" style="width: 23px; height: auto; vertical-align: top; margin-right: 5px; margin-left: 40px;">
            Code
        </a>
    </p>
    <p style="text-align: center; margin-bottom: 20px;">Accepted for publication @ 
    <a href="https://neurips.cc/Conferences/2024" target="_blank"> NeurIPS (2024).</a> <p>
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
    </p>
    <p style="text-align: justify; margin-bottom: 20px; font-size: 17px">
    Using this approach, we construct a multi-subject model trained on the combined data from 21 subjects performing 
    a behavioral task. We demonstrate that our model is able to decode the trial-wise response time of the subjects 
    during the behavioral task solely from neural data. We also show that the neural representations learned by 
    pretraining our model across individuals can be transferred in a few-shot manner to new subjects. This work 
    introduces a scalable approach towards sEEG data integration for multi-subject model training, paving the way for
    cross-subject generalization for sEEG decoding.  
    </p>
    <h5 style="margin-top: 30px">Dataset</h5> 
    <hr />
    <p style="text-align: justify; font-size: 17px">
    <strong> Dataset. </strong> We obtained neural recordings from 21 subjects that were implanted with sEEG electrodes as part of
    their medical care. Based on clinical needs, each subject was implanted with a variable number of electrodes at district locations in
    their brain (Fig. 1A, B). Subjects were mixed in terms of sex (8 male, 13 female), age (ranging from 16-57 years old), and ethnic background. 
    </p>
    <p style="; font-size: 17px">
    <strong> Behavioral Task. </strong> Subjects completed a repetitive, reaction
    time task while their sEEG was simultaneously recorded (Fig. 1C). In each trial of the task, a visual stimulus was presented. After a variable delay, the stimulus changed color. 
    At that time, the participant responded by pressing a button as fast as they could.
    </p>
    <!-- Figure with Caption -->
    <!-- Centered Figure with Limited Width -->
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/electrode_placement.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 80%; height: auto;">
        <figcaption style="text-align: center; font-size: 17px; margin-top: 5px;">
        Figure 1. <strong> Dataset and behavioral experiment. </strong> <strong>(A)</strong> Electrode placement for 4 example subjects 
        in our cohort. <strong>(B)</strong> All electrodes of all subject projected onto an MNI brain template.
        <strong>(C)</strong> Schematic of a trial of the behavioral task.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px">Objective & challenges</h5>
    <hr />
    <p style="; font-size: 17px">
    <strong> Objective. </strong> Decode the trial-wise response time of the subjects using their sEEG.
    </p>
    <p style="margin-top: 20px; margin-bottom: 10px ;font-size: 17px"> <strong>Challenges. </strong> </p>
    <ul style="; font-size: 17px">
      <li><strong>Variability of electrode number/placement across subjects: </strong> Subjects were implanted with
        sEEG electrodes as part of their medical care. The number and placement of electrodes was determined solely based on
        clinical needs. Therefore, there is no clear correspondence between the neural activity recorded 
        between individuals.  
        </li>
      <li><strong>Limited amount of per-subject data:</strong> The amount of time that each subject devoted to
        the behavioral task was limited, based on clinical circumstances. Therefore, the amount of data available to
        train models from each subject is small. This is a barrier to scaling up models, which require a lot of data
        to generalize effectively. </li>
      <li><strong>Variability in behavioral outcomes across subjects:</strong> The response time statistics 
        (mean and variance of response times across trials) of each subject are unique, posing a significant challenge
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
        the response time of the subject for each trial (Fig. 2). The electrical activity of those electrodes was then used for
        response time decoding.
    </p>
    <div style="text-align: center;">
        <img src="{{ 'assets/images/etc/responsive_electrodes.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 60%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; font-size: 17px">
        Figure 2. <strong> Neural activity for color-change responsive electrodes during task for an example subject. </strong> Each dot on the 
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
    We built this map using the network show in Fig. 3, composed of the following building blocks:
    <ul style="; font-size: 17px">
    <li>
    <strong> Tokenizer: </strong> We use a CNN that operates on each electrode separately to tokenize the neural 
    activity of each electrode.
    </li>   
    <li>
    <strong> Self-attention in time: </strong> Having tokenized the neural activity, we process the tokens with 
    self-attention <a href="https://doi.org/10.48550/arXiv.1706.03762" target="_blank"> 
    [Vaswani et al. (2017)] </a> in the time dimension, to capture long term dependencies between timepoints.
    </li>
    <li>
    <strong> Spatial positional encoding: </strong> Using MNI coordinates, we add information about each
    electrodes location in the brain to the tokens.
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
                Figure 3. <strong>Network architecture</strong>. 
            </figcaption>
        </figure>
    </div>
    <h5 style="margin-top: 30px"> Single- and multi-subject model results </h5> 
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
    training on single subjects (Fig. 4A).
    </p>
    <p style="text-align: justify; font-size: 17px">
    <strong> Finetuning the multi-subject model to single subjects. </strong> We then tested whether 
    finetuning the multi-subject model to individual subjects would further boost the performance gains.
    <strong> The multi-seubject model, finetuned to each subject achieved an average per-subject test set
    $R^2$ score of 0.41 $\pm$ 0.05 </strong>. Finetuning the multi-subject model to individual subjects boosted the
    performance gains by $\Delta R^{2}$ = 0.11, on average, compared to single subject models (Fig. 4B).
    </p>
    <div style="text-align: center; margin-top: 30px">
        <img src="{{ 'assets/images/etc/ms_vs_ss.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 4. <strong> Comparing decoding performance between </strong> <strong> (A) </strong> single-subject vs multi-subject model and <strong> (B) </strong>
        single-subject vs finetuned, multi-subject model. 
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Transferring multi-subject models to new subjects </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 30px; font-size: 17px">
    <strong> Transferring the multi-subject model to new subjects. </strong> 
    We were interested in identifying whether the multi-subject models can efficiently be transferred to new subjects, 
    unseen from the model during training. To test this, we employed a leave-one-out cross validation approach. We trained 21 models, each of which was
    trained on the combined data of all subjects but one. The weights of the pretrained models were then used as
    the basis for finetuning on the data of each left-out participant.
    <strong> Across subjects, the  models trained on other subjects and finetuned to a new one achieved an average test set
    $R^{2}$ of 0.38 $\pm$ 0.05 (mean $\pm$ sem). </strong> The finetuned single-subject models showed a
    decoding performance increase $\Delta R^{2}$ = 0.08 compared to the single-subject models trained from scratch (Fig. 5A) and 
    showed decoding performance similar to the multi-subject model (Fig. 5B).
    </p>
    <div style="text-align: center; margin-top: 20px">
        <img src="{{ 'assets/images/etc/ss_ssf.png' | relative_url }}" alt="Descriptive text for the image" style="max-width: 65%; height: auto;">
        <figcaption style="text-align: center; font-size: 16px; margin-top: 5px; max-width: 100%; font-size: 17px">
        Figure 5. <strong> Comparing decoding performance between </strong> <strong> (A) </strong> transferred 
        single-subject finetuned models vs  single-subject models trained from scratch, and <strong> (B) </strong> 
        transferred single-subject finetuned models vs the multi-subject model.
        </figcaption>
    </div>
    <h5 style="margin-top: 30px"> Baseline comparisons </h5> 
    <hr />
    <p style="text-align: justify; margin-top: 20px; font-size: 17px">
    To ensure that our modeling approach is worth the computational complexity, we compared our models against
    various simple and state-of-the-art baselines. <strong> Our proposed architecture outperformed all baseline models when 
    trained on either single or multiple subjects. </strong> 
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
    author={Georgios Mentzelopoulos and Evangelos Chatzipantazis and Ashwin G. Ramayya and Michelle J. Hedlund and Vivek P. Buch and Kostas Daniilidis and Konrad P. Kording and Flavia Vitale},
    booktitle={Thirty-eighth Conference on Neural Information Processing Systems},
    year={2024},
    }</code></pre>
    </div>
    </div>
<!--/div-->


