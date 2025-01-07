<div align="center">
<h2>General HD Map Detection with SD Map Prior Distribution</h2>

**Ziming Liu**<sup>1</sup> · **Leichen Wang**<sup>1</sup> · **Xingtao Hu**<sup>1</sup> · **Ge Yang**<sup>1</sup> · **Xinrun Li**<sup>1</sup> <br>

<sup>1</sup>Bosch Corporate Research <br>

<!-- > **submitted to IEEE Robotics and Automation Letters** -->

</div>

<!-- >
[\[Arxiv\]](https://arxiv.org/abs/2401.06614) [\[Paper\]](https://arxiv.org/pdf/2401.06614.pdf) [\[Project Page\]](https://[vveicao.github.io/projects/Motion2VecSets/](https://github.com/xiaowang12345/OMG_SD_map_prior_distribution))
-->

![teaser](./assets/teaser.png)

<p>
Visual-based high-definition (HD) map detection has become a crucial component of map-free autonomous driving systems. The most effective solutions currently utilize a query-based Bird-eye View (BEV) Transformer model. During the training phase, not only the model parameters are optimized, but also a map query embedding is optimized to learn the HD map distribution of the training data. However, this learned query embedding can not generalize well to any new data domain out of training distribution. To achieve a general HD map detection, this paper introduces the concept of standard-definition (SD) map prior distribution. SD map prior can help to build a general and domain-free map distribution with the proposed map query bank. 
</p>

![mainimage](./assets/main_pic.png)

<p>
To effectively incorporate the SD map prior, we explore the properties of SD map data and the representation of map queries. Finally, a new rule-based post-processing module is proposed to provide more reliable results by combining it with data-based model. Extensive experiments demonstrate that our proposed method enhances both the accuracy and efficiency of HD map detection by generalizing the map distribution using the SD map prior.
</p>


## extended and manual labeled SDMap subset for OpenLaneV2 dataset 

Through meticulous investigation, we have identified three primary issues within the 850 training and validation scenes provided by OpenLaneV2 regarding the SDMap.

First, there is a significant false negative (FN) problem arising from the low coverage of ground truth high-definition maps. Specifically, certain roads in the real world, such as Road A, are present in the navigation maps but lack corresponding information in the high-definition maps. This discrepancy can lead to incomplete navigational guidance and potential navigation errors.

Second, false positives (FP) occur due to updates in the navigation maps. For instance, Road A may exist in the high-definition map, but changes in the real world render it untraceable in the SDMap, thus creating inconsistencies between the maps and potentially misleading users.

Finally, the absence of human verification in crowd-sourced open navigation maps results in semantic information loss and inaccuracies. Common issues include discrepancies in lane counts, where the number provided in the navigation map does not align with reality, or even the complete omission of lane information. Addressing these challenges is essential for improving the reliability and usability of navigation systems.  Pls refer to Fig. XXX

To address these issues, we have meticulously designed an SD map verification and correction toolchain. This toolchain enables us to perform a semi-automated comparison between the ground truth high-definition maps and the SD map, allowing for systematic correction of SD map errors on a scene-by-scene basis. By facilitating this process, we aim to enhance the accuracy and reliability of navigation maps, ultimately improving user experience and operational effectiveness.  

add Toolchain xxx.png


You can directly get the original OpenLaneV2 dataset from the [[Google Drive](https://drive.google.com/file/d/10FUIrxqSPai6eQlqlgIkmBjvtBAyCmJT/view?usp=drive_link)](https://github.com/OpenDriveLab/OpenLane-V2). 

Then, you can download our extended SDMap subset from the  [Google Drive](https://drive.google.com/file/d/10FUIrxqSPai6eQlqlgIkmBjvtBAyCmJT/view?usp=drive_link). 


## Qualitative analysis of extended sdmap subset


The following images showcase the comparison between the original SDMap and the modified SDMap for four different scenarios.

- **Gray dashed lines** represent the ground truth HDMap.
- **Colored solid lines** represent the SDMap.

---

#### Scenario 1:
![Results Comparison 1](./figs/results_compare_1.png)

---

#### Scenario 2:
![Results Comparison 2](./figs/results_compare_2.png)

---

#### Scenario 3:
![Results Comparison 3](./figs/results_compare_3.png)

---

### Using GUI to Edit SDMap

This section explains the step-by-step process of editing an SDMap using the GUI interface. Below are the detailed steps:

---

#### 1. Basic Interface

The GUI provides a user-friendly interface to load and edit SDMaps. Upon starting the application, you will see the following main screen:

![Basic Interface](./figs/gui1.png)

---

#### 2. Select `log_id`

Select the desired `log_id` corresponding to the specific SDMap you wish to edit.

![Select Log ID](./figs/gui2.png)

---

#### 3. Edit the Number of Lanes

Select a road in the map to modify the lane number. The lane number field is editable, allowing you to input the correct number of lanes.

![Edit Lane Number](./figs/gui3.png)

---

#### 4. Delete a Road

To remove a road from the map, select the road and click the **Delete Road** button.

![Delete Road](./figs/gui.png)

---

#### 5. Save Edited Lane Numbers

After making changes to the lane numbers or deleting roads, the updated information will be written back to the SDMap.

![Save Edited Lane Numbers](./figs/gui5.png)
![Save Edited Lane Numbers](./figs/gui4.png)

---

#### 6. Jump to the Next `log_id`

Once you've finished editing the current `log_id`, click the **Next** button to proceed to the next map for editing. This allows for efficient processing of multiple maps.

![Jump to Next Log ID](./figs/gui6.png)
![Jump to Next Log ID](./figs/gui7.png)

---
