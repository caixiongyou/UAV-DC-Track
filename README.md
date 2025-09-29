# UAV-DC-Track

[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-blue)]()
[![Python](https://img.shields.io/badge/Python-3.9%2B-green)]()
[![Pytorch](https://img.shields.io/badge/PyTorch-2.2%2B-red)]()
[![License](https://img.shields.io/badge/License-MIT-orange)]()

## 📖 News

Data-centric is a novel perspective for UAV-based tracking: A new
 benchmark via efficient data utilization strategy


- 29 Sep 2025:  our code is available now
- We first critique the limitations
 of existing datasets and propose a novel data mining strategy that leads to the development of the
 UAVSOT dataset. 
- The UAVSOT dataset, curated
 through a meticulous selection of challenging sequences
 from general scenario datasets, serves as a testament to
 this approach, significantly improving tracking accuracy and
 robustness. 




## 🚀 Create the environment

**Option**: Use the Anaconda
```
conda create -n uav_dc_track python=3.9
conda activate uav_dc_track
bash install.sh
```

## 🚀 Data Preparation


   Follow [stark](https://github.com/researchmm/Stark) and [ostrack](https://github.com/botaoye/OSTrack) frameworks to set your datasets


## 🚀 Project File Directory


   Project file directory should be like

   ```
   ${YOUR_PROJECT_ROOT}
        -- experiments
            |-- lightfc
        -- external
            |-- vot20st
        -- lib
            |--models
            ...
        -- outputs (download and unzip the output.zip to obtain our checkpoints and row results)
            |--checkpoints
                |--...
            |--test
                |--...
        -- pretrained_models (if you want to train lightfc, put pretrained model here)
            |--mobilenetv2.pth (from torchvision model)
            ...    
        -- tracking
            ...
   ```


## 🚀 Train


   Training with multiple GPUs using DDP
```
python tracking/train.py --script LightFC --config mobilnetv2_p_pwcorr_se_scf_sc_iab_sc_adj_concat_repn33_se_conv33_center_wiou --save_dir . --mode multiple --nproc_per_node 2 
```


## 📊 Test and evaluate
Go to **tracking/test.py** and modify the parameters
```
python tracking/test.py
```

Then go to **tracking/analysis_results.py** and modify the parameters
```
python tracking/analysis_results.py
```
## 📊 Test FLOPs, Params, and Speed
```
# Params and FLOPs
python tracking/profile_model.py
# Speed
python tracking/speed.py
```










## 🙏 Acknowledgments

Codes of this project refer to the following excellent open source projects：
- [LightFC](https://github.com/LiYunfengLYF/LightFC)
- [stark](https://github.com/researchmm/Stark)
- [ostrack](https://github.com/botaoye/OSTrack)

* Thanks for the above open source projects, which helps us to quickly implement our ideas.


