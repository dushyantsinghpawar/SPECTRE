<div align="center">

  # SPECTRE: Visual Speech-Aware Perceptual 3D Facial Expression Reconstruction from Videos

[![Paper](https://img.shields.io/badge/arXiv-2207.11094-brightgreen)](https://arxiv.org/abs/2207.11094)
&nbsp; [![Project WebPage](https://img.shields.io/badge/Project-webpage-blue)](https://filby89.github.io/spectre/)
&nbsp; <a href='https://youtu.be/P1kqrxWNizI'>
      <img src='https://img.shields.io/badge/Youtube-Video-red?style=flat&logo=youtube&logoColor=red' alt='Youtube Video'>
    </a>
</div>

<p align="center"> 
<img src="samples/visualizations/M003_level_1_angry_014_grid.gif">
<img src="samples/visualizations/test_BImnT7lcLDE_00003_grid.gif">
</p>


<p align="center"> 
<img src="cover.png">
</p>
<p align="center"> Our method performs visual-speech aware 3D reconstruction so that speech perception from the original footage is preserved in the reconstructed talking head. On the left we include the word/phrase being said for each example. <p align="center">

This is the implementation of the paper adapted from its official pytorch implementation:
  
```
Visual Speech-Aware Perceptual 3D Facial Expression Reconstruction from Videos
Panagiotis P. Filntisis, George Retsinas, Foivos Paraperas-Papantoniou, Athanasios Katsamanis, Anastasios Roussos, and Petros Maragos
arXiv 2022
```



## Installation
Clone the repo and its submodules:
```bash
git clone --recurse-submodules -j4 https://github.com/dushyantsinghpawar/SPECTRE
cd SPECTRE
```  

You need to have installed a working version of Pytorch with Python 3.6 or higher and Pytorch 3D. You can use the following commands to create a working installation:
```
pip install -r requirements.txt # install the rest of the requirements
```

Installing a working setup of Pytorch3d with Pytorch can be a bit tricky. It is part of the requirements.txt file. We are downloading its implementation from Github Provided by [FacebookResearch](https://github.com/facebookresearch/pytorch3d.git).

After installing make the following changes in the "chumpy" library package (generally you can find it in "/usr/local/lib/python3.10/dist-packages/chumpy/init.py'"):
Replace the "numpy" part of the code with the code given below:
```
from numpy import nan, inf
bool = bool
int = int
float = float
complex = complex
object = object
unicode = str
str = str
```

Install the face_alignment and face_detection packages:
```bash
cd external/face_alignment
pip install -e .
cd ../face_detection
git lfs pull
pip install -e .
cd ../..
```
Before implementing the "git lfs pull" You may need to install git-lfs to run the above commands. [More details](https://stackoverflow.com/questions/48734119/git-lfs-is-not-a-git-command-unclear)  
```bash
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
sudo apt-get install git-lfs
```
Download the FLAME model and the pretrained SPECTRE model:
```bash
pip install gdown
bash quick_install.sh
```

## Demo
Samples are included in ``samples`` folder. You can run the demo by running 

```bash
python demo.py --input samples/LRS3/0Fi83BHQsMA_00002.mp4 --audio
```

The audio flag extracts audio from the input video and puts it in the output shape video for visualization purposes (ffmpeg is required for video creation).


## Acknowledgements
This repo is has been heavily based on the original implementation of [spectre](https://github.com/filby89/spectre.git). We also acknowledge the following 
repositories which we have benefited greatly from as well:

- [DECA](https://github.com/YadiraF/DECA/)
- [EMOCA](https://github.com/radekd91/emoca)
- [face_alignment](https://github.com/hhj1897/face_alignment)
- [face_detection](https://github.com/hhj1897/face_detection)
- [Visual_Speech_Recognition_for_Multiple_Languages](https://github.com/mpc001/Visual_Speech_Recognition_for_Multiple_Languages)

## Citation
If your research benefits from this repository, consider citing the following:

```
@misc{filntisis2022visual,
  title = {Visual Speech-Aware Perceptual 3D Facial Expression Reconstruction from Videos},
  author = {Filntisis, Panagiotis P. and Retsinas, George and Paraperas-Papantoniou, Foivos and Katsamanis, Athanasios and Roussos, Anastasios and Maragos, Petros},
  publisher = {arXiv},
  year = {2022},
}
```
  
  
