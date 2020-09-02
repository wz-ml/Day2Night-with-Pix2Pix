# Day2Night-with-Pix2Pix
![](https://github.com/wz-ml/Day2Night-with-Pix2Pix/blob/master/visualization.png?raw=true)

A day-to-night image translation implementation using Pix2Pix. The model was trained on the University of Maryland's DNIM dataset for 100 epochs, and actually achieved a pretty good result (at least visually). Credit goes to [affinelayer](https://github.com/affinelayer/pix2pix-tensorflow) for the tensorflow pix2pix package.
Check out [Day2Night.ipynb](https://github.com/wz-ml/Day2Night-with-Pix2Pix/blob/master/Day2Night.ipynb) for the code!

### Dataset Source
[Evaluating Local Features for Day-Night Matching](http://users.umiacs.umd.edu/~hzhou/dnim.html) - University of Maryland, College Park, USA.
### Installation
#### Through cloning
- `Git clone` this repository (through Github desktop or through the link).
- Open Day2Night.ipynb
- Run codeblocks sequentially until `!python pix2pix.py \`.
#### Alternatively
- Go to this [Colab link] (https://colab.research.google.com/github/wz-ml/Day2Night-with-Pix2Pix/blob/master/Day2Night.ipynb)
- Click <b>Copy To Drive</b>
- Run codeblocks sequentially until `!python pix2pix.py \`.
### Training
- Run `!python pix2pix.py \ --mode train \`
- OPTIONAL: Change input/output folders and training Epochs.
### Visualization
```
# test the model
!python pix2pix.py \
  --mode test \
  --output_dir daynight_test \
  --input_dir daynight/val \
  --checkpoint daynight_train
  ```
```
import matplotlib.pyplot as plt
import numpy as np
choice = random.randint(0,150)
path = "/content/pix2pix-tensorflow/daynight_test/images/"
fig = plt.figure(figsize=(14,18))
axarr = fig.subplots(1,3)
[ax.axis('off') for ax in axarr]
axarr[0].imshow(Image.open(path + ('image%d'%choice) + '-inputs.png'))
axarr[0].set_title("Input",size=15,color='white',weight='bold')
axarr[1].imshow(Image.open(path + ('image%d'%choice) + '-outputs.png'))
axarr[1].set_title("Reconstruction",size=15,color='white',weight='bold')
axarr[2].imshow(Image.open(path + ('image%d'%choice) + '-targets.png'))
axarr[2].set_title("Original",size=15,color='white',weight='bold')
plt.show()
```
### License
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
- **[MIT license](http://opensource.org/licenses/mit-license.php)**
