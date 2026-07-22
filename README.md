# Antimicrobial activity prediction against Enterobacter spp. from public ChEMBL data

Bioactivity prediction of growth inhibition in Enterobacter spp., trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (ACTIVITY) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-06-02.

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
- **Output Dimension:** `6`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Enterobacter spp. from 5 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 5 sub-models. Recommended threshold: 0.637. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point low-data catch-all pool of 39 assays (191 compounds). Recommended threshold: 0.705. |
| chembl_dose_response_0 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 77 assays (1284 compounds). Recommended threshold: 0.498. |
| chembl_dose_response_1 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 111 assays (1281 compounds). Recommended threshold: 0.699. |
| chembl_dose_response_2 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 67 assays (634 compounds; incl. 132 added negatives). Recommended threshold: 0.563. |
| chembl_dose_response_3 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 65 assays (492 compounds; incl. 91 added negatives). Recommended threshold: 0.51. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos9bpi](https://hub.docker.com/r/ersiliaos/eos9bpi)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos9bpi.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos9bpi.zip)

### Resource Consumption
- **Model Size (Mb):** `47`
- **Environment Size (Mb):** `7208`
- **Image Size (Mb):** `2080.77`

**Computational Performance (seconds):**
- 10 inputs: `41.37`
- 100 inputs: `39.87`
- 10000 inputs: `746.27`

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
