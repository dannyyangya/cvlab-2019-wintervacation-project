# cvlab-2019-wintervacation-project

**This project is supported by [amoshyc](https://github.com/amoshyc), and mainly modifies from [his example](https://github.com/amoshyc/cvlab-2019w-project)**

## Task

Given 5000 images of car [^1] (312MB), detect the license plate and unwarp it.

Each image is guaranteed with 1 license plate.

The ground truth and metadata are encoded in the name of each image.

To download & uncompress the dataset:

~~~
$ wget https://github.com/amoshyc/cvlab-2019w-project/releases/download/v0.1/ccpd5000.tar.gz
$ tar zxvf ccpd5000.tar.gz
$ ls ccpd5000/**/*.jpg | wc -l # expected 6000 (5000 train/valid + 1000 test)
~~~

[^1]: This is a subset of [CCPD](https://github.com/detectRecog/CCPD) dataset.
