# Antimicrobial activity prediction against Enterobacter spp. from public ChEMBL data

Bioactivity prediction of growth inhibition in Enterobacter spp., trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to dose-response (MIC) assays. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-05-21.

## Information
### Identifiers
- **Ersilia Identifier:** `eos9bpi`
- **Slug:** `antimicrobial-activity-enterobacter`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Antimicrobial resistance`
- **Target Organism:** `Enterobacter spp`
- **Tags:** `Gram-negative bacteria`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `7`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Enterobacter spp from 6 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 6 sub-models. Recommended threshold: 0.924. |
| merged_mic_decoys_c | float | high | Probability from sub-model trained on MIC measurements merged across 3 ChEMBL assays (cutoff 10 uM; n=1060 incl. decoys). Recommended threshold: 0.889. |
| merged_mic_decoys_b | float | high | Probability from sub-model trained on MIC measurements merged across 3 ChEMBL assays (cutoff 10 uM; n=1050 incl. decoys). Recommended threshold: 0.899. |
| merged_mic_decoys_d | float | high | Probability from sub-model trained on MIC measurements merged across 12 ChEMBL assays (cutoff 10 uM; n=780 incl. decoys). Recommended threshold: 0.907. |
| merged_mic_decoys_a | float | high | Probability from sub-model trained on MIC measurements merged across 9 ChEMBL assays (cutoff 10 uM; n=660 incl. decoys). Recommended threshold: 0.845. |
| general_mic | float | high | Probability from sub-model trained on MIC measurements aggregated across 939 ChEMBL assays (cutoff 10 uM; n=3997). Recommended threshold: 0.519. |
| general_mic90_decoys | float | high | Probability from sub-model trained on MIC90 measurements aggregated across 86 ChEMBL assays (cutoff 10 uM; n=750 incl. decoys). Recommended threshold: 0.866. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos9bpi](https://hub.docker.com/r/ersiliaos/eos9bpi)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos9bpi.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos9bpi.zip)

### Resource Consumption
- **Model Size (Mb):** `28`
- **Environment Size (Mb):** `1888`
- **Image Size (Mb):** `2067.4`

**Computational Performance (seconds):**
- 10 inputs: `41.17`
- 100 inputs: `35.56`
- 10000 inputs: `598.8`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos9bpi
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos9bpi
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
