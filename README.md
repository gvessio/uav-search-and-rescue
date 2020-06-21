# Search-and-rescue from drones with Computer Vision

In this repository, we provide a new dataset for search-and-rescue (SAR) operations from drones. As it is small-sized, the dataset is currently intended for testing and evaluation purposes only. We also provide baseline results on these data, obtained with the state-of-the-art object detector TinyYOLOv3. It can return (nearly) real-time responses on embedded GPUs currently mounted on drones. We used the pre-trained model provided in the well-known Alexey's repository, fine-tuning it on the training set of Task 1 (object detection) of VisDrone, focusing only on people. Fine-tuning has been performed until early stopping, by monitoring the loss value on the validation set of the same dataset.

Actually, the dataset comprises two different SAR scenarios: 
- dataset1: mountains (200 frames, 100 with annotated people, 100 without people)
- dataset2: islands (111 frames, ? with annotated people, ? without people)

Frames are annotated in accordance with some well-known standards. Each text file stores the annotations of the corresponding frame, with each line representing the single object (person, in this case). The format of each line is as follows:

<object_category>,<bbox_left>,<bbox_top>,<bbox_width>,<bbox_height>

where <bbox_left> and <bbox_top> represent the x and y coordinate of the top-left corner of the ground truth bounding box, while <bbox_width> and <bbox_height> indicate its width and height in pixels. <object_category> indicates the type of annotated object. It currently equals 0, since only the people category is considered. However, it may be extended with further categories in future realeses.

Any contribution to make the dataset bigger is welcome!

**Contributors**: Giovanna Castellano, Davide Carone, Francesco Scigliuto, Gennaro Vessio
