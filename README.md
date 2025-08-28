# Cross-Domain Generalizability of Deep Learning Models in Predictive Business Process Monitoring (PBPM)

## Overview
This project investigates the **cross-domain transferability of deep learning models** for Predictive Business Process Monitoring (PBPM).  
Traditional PBPM models achieve high accuracy in their training domains but often fail when applied to other organizational domains due to differences in activity vocabularies and process structures.  

I systematically evaluated **BiLSTM, BiGRU, and Transformer architectures** across cross-domain scenarios, introducing synthetic dataset modifications to control **vocabulary overlap** and **structural similarity**.  
Findings highlight that **vocabulary overlap (minimum 30%)** is critical for effective transfer, with **BiGRU** demonstrating the strongest generalization capabilities.

---

## Objectives
- Assess the **cross-domain performance** of BiLSTM, BiGRU, and Transformer models.  
- Identify thresholds for **vocabulary overlap** and **structural similarity** that enable transferability.  
- Provide a **controlled methodology** for cross-domain evaluation through dataset modifications.  
- Develop practical **guidelines for organizations** deploying PBPM across multiple domains.  

---

## Key Challenges
- **Vocabulary gap**: Different domains use distinct activity labels.  
- **Structural disparity**: Workflow length and complexity vary across domains.  
- **Model overfitting**: Complex architectures fail to adapt to unseen process patterns.  

---

## Methodology
1. **Datasets**  
   - **BPIC 2012** (Financial loan application process) – 13,087 cases, 24 activities.  
   - **Helpdesk** (IT service management process) – 4,580 cases, 14 activities.  

2. **Macro-Activity Abstraction**  
   - Used **TF-IDF** + **K-means clustering** to group semantically similar activities into macro-clusters.  

3. **Synthetic Dataset Modification**  
   - Controlled **vocabulary overlap** (0%, 30%, 60%).  
   - Controlled **structural similarity** (0%, 30%, 60%).  

4. **Model Architectures**  
   - **BiLSTM** – bidirectional memory-based modeling.  
   - **BiGRU** – simplified recurrent architecture with fewer parameters.  
   - **Transformer** – attention-based global sequence modeling.  

---

## Results
- **Vocabulary overlap is critical**: 0% overlap → total failure (F1 ≈ 0.0).  
- **BiGRU outperformed** more complex models, retaining **52% of same-domain F1 score** under optimal transfer conditions (30% overlap + 30% similarity).  
- **Structural similarity boosts transfer** when combined with vocabulary alignment.  
- **Overfitting effect**: Higher similarity (60%) sometimes reduces transfer performance.  

| Model        | Same-Domain F1 (BPIC) | Cross-Domain Best F1 (BPIC→Helpdesk) |
|--------------|------------------------|---------------------------------------|
| BiLSTM       | 0.729                  | 0.309                                 |
| BiGRU        | 0.736                  | **0.382** (optimal)                   |
| Transformer  | 0.804                  | 0.173                                 |

---

## Implementation
The repository includes:  
- `datasets/` → Process mining event logs  
- `results/` → Experimental results and evaluation metrics  
- `final.ipynb` → End-to-end Jupyter Notebook implementation  
- `requirements.txt` → Dependencies  

---

##  Installation
```bash
# Clone the repository
git clone https://github.com/as-salad-code/PBPM-CrossDomain-Generalizability.git
cd PBPM-CrossDomain-Generalizability

# Install dependencies
pip install -r requirements.txt
```

## Usage
Run the notebook
```bash

jupyter notebook final.ipynb
```
