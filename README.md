# cvlab-2019-wintervacation-project

**This project is supported by [amoshyc](https://github.com/amoshyc), and mainly modifies from [his example](https://github.com/amoshyc/cvlab-2019w-project)**

## Task

Given 5000 images of car [^1] (312MB), to detect the license plate and unwarp it.

Each image is guaranteed with 1 license plate.

The ground truth and metadata are encoded in the name of each image.

To download & uncompress the dataset:

~~~
$ wget https://github.com/amoshyc/cvlab-2019w-project/releases/download/v0.1/ccpd5000.tar.gz
$ tar zxvf ccpd5000.tar.gz
$ ls ccpd5000/**/*.jpg | wc -l # expected 6000 (5000 train/valid + 1000 test)
~~~

[^1]: This is a subset of [CCPD](https://github.com/detectRecog/CCPD) dataset.

## My modification

1. Use higher resolution image:
    * (192, 320) ==> (240, 400)

2. Train longer: 
    * 30 epochs

3. Adjust the model structure:
    * x = self.act3(self.bn3(self.conv3(x))) # added

4. Use deeper one:
    * ConvBlock(64, 128), # added
    * nn.MaxPool2d((2, 2)), # added

5. LR decay or Lower LR, Use SGD instead of Adam:
    * optimizer = torch.optim.SGD(model.parameters(), lr = 0.01*(30-epoch)/20, momentum=0.9) # changed

6. Try other kind of loss:
    * Have tried SmoothL1Loss, BCELoss, and MSELoss. But L1Loss still have the best performance on MSE in this case.

## Testing result

   * MSE of each corner:

      * BR: 0.0002553341970499999

      * BL: 0.0001913923876

      * TL: 0.00019788152704999993

      * TR: 0.00025003787874999984

   * mMSE: 0.00022366149761249992

### Testing images
![](/testimage/000_vis.jpg)

![](/testimage/099_vis.jpg)
