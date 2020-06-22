# Search-and-rescue from drones with Computer Vision

## Motivations

Unmanned aerial vehicles (UAVs), most commonly known as drones, are increasingly used as a technological support tool for search-and-rescue (SAR) operations (and post-disaster area explorations as well). UAVs equipped with high-resolution cameras and embedded, yet powerful GPUs, in fact, can provide an effective and efficient aid to emergency rescue operations, mainly because locating victims, which may be unconscious or injured, as much fast as possible, is crucial to improve their chance of survival.

In particular, the use of drones that are able to automatically detect people in the scenes can increase detection rate, while reducing rescue time. This goal motivates research efforts towards the development of real-time intelligent decision support tools, to be mounted directly on-board drones. Unfortunately, there is currently a small body of knowledge on the application of machine/deep learning and computer vision algorithms to this kind of problem. Moreover, the existing works make use of images captured from drones depicting unrealistic, from a SAR perspective, everyday life scenarios. Having sufficiently large and representative datasets for training and testing is crucial for developing effective detection models.

## Objectives

In this repository, we provide a new dataset specifically conceived for SAR operations from drones with computer vision. As it is small-sized, the dataset is currently intended for testing and evaluation purposes only. We also provide baseline results on these data, obtained with the state-of-the-art object detector TinyYOLOv3. This detector can return (nearly) real-time responses on embedded GPUs currently mounted on drones. We used the pre-trained model provided in the well-known [Alexey's repository]("https://github.com/AlexeyAB"), and we fine-tuned it on the challenging training set of Task 1 (object detection) of [VisDrone]("https://github.com/VisDrone"), focusing only on people. Fine-tuning has been performed until early stopping, by monitoring the loss value on the validation set of the same dataset.

### Dataset description

Actually, the dataset comprises two different SAR scenarios 
- `mountains`: 200 frames, 100 with annotated people, 100 without people
- `beaches`: 110 frames, 55 with annotated people, 55 without people

Frames are annotated in accordance with some well-known standards. Each text file stores the annotations of the corresponding frame, with each line representing the single object (person, in this case). The format of each line is as follows:

`<object-category> <x> <y> <width> <height>`

where `<x>` and `<y>` represent the *x* and *y* coordinate of the center of the ground truth bounding box, while `width` and `height` indicate its width and height, respectively. These are float values relative to the original proportions of the frame in pixels, in accordance with some annotation standards, such as that required by the YOLO family. `object-category` indicates the type of annotated object. It currently equals `1`, since only the people category is considered. However, it may be extended with further categories in future releases.

The main aim of this repository is to encourage contributions on this intriguing topic. In particular, any contribution to make the dataset bigger is welcome!

### Baseline results

The following are the precision-recall curves for the `mountains` and `beaches` datasets separately.

<img src="/baseline_results/precision-recall_curve_mountains.png" width="400" height="auto"> <img src="/baseline_results/precision-recall_curve_beaches.png" width="400" height="auto">

The following, instead, is the same curve obtained by evaluating TinyYOLOv3 on the overall data. 

<img src="/baseline_results/precision-recall_curve_overall.png" width="400" height="auto">

The trained model's weights are provided in the main folder.

#### Original contributors

Giovanna Castellano, Davide Carone, Francesco Scigliuto, Gennaro Vessio (from the University of Bari "Aldo Moro", Italy). Any question can be emailed to <gennaro.vessio@uniba.it>.
