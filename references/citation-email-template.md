# Citation email template

Use this structure by default. Fill bracketed fields with paper-specific details.

The user-preferred output starts with `Suggestion for your arXiv:[target-id]` as the visible heading, then the email body. Do not replace this with generic headings like `To:` or `Subject:` unless the user explicitly asks for email-client fields.

Before the email body, list the recipient email only if it has been verified from arXiv source, the paper/PDF, an author page, or an institutional profile. Include the source, e.g. `收件人：name@example.edu（来源：arXiv source main.tex）`. If no email is verified, write `收件人：未查到可靠邮箱` and do not guess.

```text
Suggestion for your arXiv:[target-id]

Dear Dr. [Surname] [and co-authors],

Congratulations on your very interesting work, "[target title]" (arXiv:[target-id]). I was particularly impressed by [specific technical contribution, validation, dataset, method, or application], as well as [second concrete strength if useful].

In parallel, we have been exploring [related direction]. In our paper, "[user paper title]" (arXiv:[user-id]), we [one-sentence description of what the work does]. If there is a second closely related paper, add: In another recent study, "[second title]" (arXiv:[second-id]), we [one-sentence description].

Given the shared theme of [specific shared methodology or scientific problem], we would be very grateful if you would consider citing our related work(s) in a future revision.

We will continue to follow your research with great interest.

Best regards,
Tian-Yang Sun
College of Sciences, Northeastern University
```

## Style notes

- Prefer `Congratulations on your very interesting work` for the opening.
- The praise must be concrete; name the method, data, validation, or result.
- The second paragraph should include exact titles and arXiv IDs, not only vague descriptions.
- The request paragraph should be short and humble.
- Do not over-argue the citation fit; one clear shared-theme sentence is enough.

## User-approved examples

Follow these examples closely for phrasing, paragraph order, and sign-off.

### Current glitch-inference example

```text
收件人：chowdm4@rpi.edu, soumya.mohanty@utrgv.edu（来源：arXiv HTML 正文作者信息）

Suggestion for your arXiv:2608.29295

Dear Dr. Chowdhury, Dr. Mohanty, and collaborators,

Congratulations on your very interesting work, "Automated identification and subtraction of gravitational-wave glitches using boundary refinement" (arXiv:2608.29295). I was particularly impressed by your explicit boundary-identification methods and the demonstration that targeted subtraction can preserve 95-97% of the injected signal-to-noise ratio, substantially improving over wavelet shrinkage alone.

In parallel, we have been exploring parameter inference for gravitational-wave signals contaminated by transient noises. In our paper, "Efficient parameter inference for gravitational wave signals in the presence of transient noises using temporal and time-spectral fusion normalizing flow" (arXiv:2312.08122; Chinese Physics C 48, 045108), we developed a likelihood-free framework that combines temporal and time-frequency information to infer source parameters in the presence of glitches. In another recent study, "Robust parameter inference for Taiji via time-frequency contrastive learning and normalizing flows" (arXiv:2604.13867), we investigated glitch-robust inference for massive black-hole binaries in the Taiji configuration.

Given the shared focus on mitigating transient-noise contamination while preserving gravitational-wave information for reliable parameter estimation, we would be very grateful if you would consider citing our related works in a future revision.

We will continue to follow your research with great interest.

Best regards,
Tian-Yang Sun
College of Sciences, Northeastern University
```

### Earlier approved examples

```text
Suggestion for your arXiv:2606.00219
Dear Dr. Breitman and collaborators,

Congratulations on your very interesting work, “21cmEMUv3: a hybrid diffusion-LSTM emulator of 21cmFAST summary observables” (arXiv:2606.00219). I was particularly impressed by how your hybrid diffusion-LSTM framework emulates multiple 21cmFAST summary observables, including the 21-cm power spectrum, global signal, neutral fraction, spin temperature, UV luminosity functions, and Thomson optical depth, providing an efficient tool for inference in the cosmic dawn and epoch of reionization.

In parallel, we have also been exploring deep-learning-based inference methods for 21-cm cosmology. In our work, “Deep learning-driven likelihood-free parameter inference for 21-cm forest observations” (arXiv:2407.14298), we developed a likelihood-free inference framework to infer dark matter and intergalactic-medium properties from 21-cm forest signals, focusing on simulation-based parameter inference for non-Gaussian 21-cm observables during the cosmic dawn and reionization era.

Given the shared theme of machine-learning-assisted inference for 21-cm cosmology and reionization, especially the use of simulation-based neural methods to extract astrophysical and cosmological information from 21-cm observables, we would be very grateful if you would consider citing our related work in a future revision.

We will continue to follow your research with great interest.

Best regards,
Tian-Yang Sun
College of Sciences, Northeastern University
```

```text
Suggestion for your arXiv:2605.30665
Dear Dr. Moreno and collaborators,

Congratulations on your very interesting work, “Quantification of the parameter estimation error from Rotating Core Collapse supernovae” (arXiv:2605.30665). I was particularly interested in your use of an analytical model for the core-bounce phase of rapidly rotating core-collapse supernovae, together with numerical waveform catalogs and simulated O4 noise, to quantify the estimation error of the rotational parameter beta through matched filtering and the Cramer-Rao lower bound.

In parallel, we have been exploring deep-learning-based methods for gravitational-wave detection from core-collapse supernovae. In our recent work, “Contrastive Self-Supervised Learning for Gravitational Wave Detection from Core-Collapse Supernovae” (arXiv:2605.21310), we developed a contrastive self-supervised convolutional autoencoder framework for CCSN GW detection, aiming to improve the robustness of signal representation and detection performance for weak and model-dependent CCSN waveforms.

Given the shared focus on core-collapse supernova gravitational waves, and the complementarity between your parameter-estimation analysis of rotating core-bounce signals and our machine-learning-based CCSN GW detection framework, we would be very grateful if you would consider citing our related work in a future revision.

We will continue to follow your research with great interest.

Best regards,
Tian-Yang Sun
College of Sciences, Northeastern University
```
