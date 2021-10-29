# SinGAN

## Random samples from a *single* image
With SinGAN, you can train a generative model from a single natural image, and then generate random samples from the given image, for example:

![](imgs/teaser.PNG)


## SinGAN's applications
SinGAN can be also used for a line of image manipulation tasks, for example:
 ![](imgs/manipulation.PNG)
This is done by injecting an image to the already trained model. 

## Code

### Install dependencies

```
python -m pip install -r requirements.txt
```

This code was tested with python 3.6, torch 1.4

Please note: the code currently only supports torch 1.4 or earlier because of the optimization scheme.


###  Train
To train SinGAN model on your own image, put the desired training image under Input/Images, and run

```
python main_train.py --input_name <input_file_name>
```

This will also use the resulting trained model to generate random samples starting from the coarsest scale (n=0).

To run this code on a cpu machine, specify `--not_cuda` when calling `main_train.py`

###  Random samples
To generate random samples from any starting generation scale, please first train SinGAN model on the desired image (as described above), then run 

```
python random_samples.py --input_name <training_image_file_name> --mode random_samples --gen_start_scale <generation start scale number>
```

pay attention: for using the full model, specify the generation start scale to be 0, to start the generation from the second scale, specify it to be 1, and so on. 

###  Random samples of arbitrary sizes
To generate random samples of arbitrary sizes, please first train SinGAN model on the desired image (as described above), then run 

```
python random_samples.py --input_name <training_image_file_name> --mode random_samples_arbitrary_sizes --scale_h <horizontal scaling factor> --scale_v <vertical scaling factor>
```

###  Animation from a single image

To generate short animation from a single image, run

```
python animation.py --input_name <input_file_name> 
```

This will automatically start a new training phase with noise padding mode.
The data used for the user study can be found in the Downloads folder. 
