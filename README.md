# hip

Hip is an easy way to share and explore datasets.

Hip is file based. To access data, all you need to know is how to work with files. With a few simple commands or yaml config file edits you can:

* Automatically sync your data to cloud: just generate your dataset, and it will be saved to cloud.
* Easily share your dataset publicly or privately.
* Automatically maintain a backup of multiple versions of your data; never lose anything with an accidental rewrite.
* Easily sample data by instructing hip to only maintain a fraction of data on your local disk.
* Apply various transformations to data that are swiftly executed in a cloud so you don't have to wait.

## Getting Started

### Installation

Install hip by running ```pip install hip```. Then run ```pip configure```. It will ask you a few questions, and you will be done. If you need to sync / share private datesets, you will need a hip key. You can obtain it at https://hipdata.io/register

Anaconda installation is also supported. You can install hip by running ```conda install hip```.

### Syncing your dataset to cloud

```
mkdir my-dataset
cd my-dataset
hip push hip://my-orgname/my-username/my-dataset
```

This will instruct hip to sync your data to the cloud, and it will maintain 3 backup copies for all files.

### Sharing a dataset

```
mkdir my-dataset
cd my-dataset
hip pull hip://my-orgname/my-username/my-dataset
```

### Samping a dataset

```
hip pull --sample=1000 hip://my-orgname/my-username/my-dataset
```

For example, you can get a sample of 1000 images from Open Images dataset:

```
hip pull --sample=1000 hip://hipdata.io/shared/open-images-v4
```

### Preprocessing data

To crop Open Images to 100x100 pixels in the middle and then make them grayscale:

```
hip pull --sample=1000 --pre=crop-100-100-center,grayscale hip://hipdata.io/shared/open-images-v4
```

### Configuration file
Each directory set up with hip has a configuration file '.hip.yaml'. You can edit it directly.
