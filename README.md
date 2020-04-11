# GAN Attack against Federated Deep Learning

This project is the reproduction of the paper [Deep Models Under the GAN: Information Leakage from Collaborative Deep Learning](https://arxiv.org/pdf/1702.07464.pdf). The details of this project are not exactly the same as the paper, but it can show the effect of this kind of attack, which uses gan to capture the information of other participants' data.

This reproduction assumes that there're 10 clients patcipating the training, and each one of them has a certain class of data.

For convience, I use the weight averaging aggregation insetead of choosing certain portion of the parameters to upload or download.

In this scenario, each paticpant owns different data, which means that their data are in non-iid condition, so the averaging aggregation seems difficult to converge, I refer the paper [Federated Learning with Non-IID Data](https://arxiv.org/pdf/1806.00582.pdf) and apply a warm-up training to the centralized model with 5% of all the data, this strategy raise the accuracy of the later training process.

Some details in the paper are not clear, for example, how many images should be generated by the generator in a epoch, do the generated images accumulate or the old generated samples will be replaced by the new ones, does the training set for the GAN contain the generated sample? Base on my experiment result, replacing the old generated samples and traning GAN on the dataset without generated images will be a little better.
