<div align="center">
    <img src='__assets__/title.png'/>
</div>

---
### ⭐️ **Our team's works:** [[**HiFlow**](https://bujiazi.github.io/hiflow.github.io/)]  [[**MotionClone**](https://bujiazi.github.io/motionclone.github.io/)]  [[**ByTheWay**](https://github.com/Bujiazi/ByTheWay)] 

## Light-A-Video: Training-free Video Relighting via Progressive Light Fusion
This repository is the official implementation of Light-A-Video. It is a **training-free framework** that enables 
zero-shot illumination control of any given video sequences or foreground sequences.

<details><summary>Click for the full abstract of Light-A-Video</summary>

> Recent advancements in image relighting models, driven by large-scale datasets and pre-trained diffusion models, have enabled the imposition of consistent lighting. However, video relighting still lags, primarily due to the excessive training costs and the scarcity of diverse, high-quality video relighting datasets. A simple application of image relighting models on a frame-by-frame basis leads to several issues: lighting source inconsistency and relighted appearance inconsistency, resulting in flickers in the generated videos. In this work, we propose Light-A-Video, a training-free approach to achieve temporally smooth video relighting. Adapted from image relighting models, Light-A-Video introduces two key techniques to enhance lighting consistency. First, we design a Consistent Light Attention (CLA) module, which enhances cross-frame interactions within the self-attention layers of the image relight model to stabilize the generation of the background lighting source. Second, leveraging the physical principle of light transport independence, we apply linear blending between the source video's appearance and the relighted appearance, using a Progressive Light Fusion (PLF) strategy to ensure smooth temporal transitions in illumination. Experiments show that Light-A-Video improves the temporal consistency of relighted video while maintaining the relighted image quality, ensuring coherent lighting transitions across frames. 
</details>

**[Light-A-Video: Training-free Video Relighting via Progressive Light Fusion]()** 
</br>
[Yujie Zhou*](https://github.com/YujieOuO/),
[Jiazi Bu*](https://github.com/Bujiazi/),
[Pengyang Ling*](https://github.com/LPengYang/),
[Pan Zhang<sup>†</sup>](https://panzhang0212.github.io/),
[Tong Wu](https://wutong16.github.io/),
[Qidong Huang](https://shikiw.github.io/),
[Jinsong Li](https://li-jinsong.github.io/),
[Xiaoyi Dong](https://scholar.google.com/citations?user=FscToE0AAAAJ&hl=en/),
[Yuhang Zang](https://yuhangzang.github.io/),
[Yuhang Cao](https://scholar.google.com/citations?hl=zh-CN&user=sJkqsqkAAAAJ),
[Anyi Rao](https://anyirao.com/),
[Jiaqi Wang](https://myownskyw7.github.io/),
[Li Niu<sup>†</sup>](https://www.ustcnewly.com/)  
(*Equal Contribution)(<sup>†</sup>Corresponding Author)

[![arXiv](https://img.shields.io/badge/arXiv-2502.08590-b31b1b.svg)](https://arxiv.org/abs/2502.08590)
[![Project Page](https://img.shields.io/badge/Project-Website-green)](https://bujiazi.github.io/light-a-video.github.io/)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Demo-red)](https://huggingface.co/spaces/fffiloni/Light-A-Video)

## 💡 Demo
[![]](https://github.com/user-attachments/assets/ea5a01b9-a5a5-4159-a61b-7fef8e44e6db)

## 📜 News

**[2025/6/26]** Happy to announce that Light-A-Video is accepted by ICCV 2025!

**[2025/3/14]** Support [CogVideoX](https://github.com/THUDM/CogVideo)!

**[2025/3/11]** Support [Wan2.1](https://github.com/Wan-Video/Wan2.1)!

**[2025/2/11]** Code is available now!

**[2025/2/10]** The paper and project page are released!

## 🏗️ Todo
- [x] Release a gradio demo.

- [x] Release Light-A-Video code with CogVideoX-2B pipeline.

## 📚 Gallery
We show more results in the [Project Page](https://bujiazi.github.io/light-a-video.github.io/).

<table class="center">
    <tr>
      <td><p style="text-align: center">..., red and blue neon light</p></td>
      <td><p style="text-align: center">..., sunset over sea</p></td>
    </tr>
    <tr>
      <td><img src="__assets__/cat_light.gif"></td>
      <td><img src="__assets__/boat_light.gif"></td>
    </tr>
    <tr>
      <td><p style="text-align: center">..., sunlight through the blinds</p></td>
      <td><p style="text-align: center">..., in the forest, magic golden lit</p></td>
    </tr>
    <tr>
      <td><img src="__assets__/man_light.gif"></td>
      <td><img src="__assets__/water_light.gif"></td>
    </tr>
</table>


## 🚀 Method Overview

<div align="center">
    <img src='__assets__/pipeline.png'/>
</div>

Light-A-Video leverages the capabilities of image relighting models and VDM motion priors to achieve temporally consistent video relighting. 
By integrating the **Consistent Light Attention** to stabilize lighting source generation and employ the **Progressive Light Fusion** strategy
for smooth appearance transitions.

## 🔧 Installations

### Setup repository and conda environment

```bash
git clone https://github.com/bcmi/Light-A-Video.git
cd Light-A-Video

conda create -n lav python=3.10
conda activate lav

pip install -r requirements.txt
```

## 🔑 Pretrained Model Preparations
- IC-Light: [Huggingface](https://huggingface.co/lllyasviel/ic-light)
- SD RealisticVision: [Huggingface](https://huggingface.co/stablediffusionapi/realistic-vision-v51)
- Animatediff Motion-Adapter-V-1.5.3: [Huggingface](https://huggingface.co/guoyww/animatediff-motion-adapter-v1-5-3)

Model downloading is automatic.

## 🎈 Quick Start

### Perform video relighting with customized illumination control
```bash
# relight
python lav_relight.py --config "configs/relight/car.yaml"
```
### Perform foreground sequences relighting with background generation
A script based on [SAM2](https://github.com/facebookresearch/sam2) is provided to extract foreground sequences from videos. 
```bash
# extract foreground sequence
python sam2.py --video_name car --x 255 --y 255

# inpaint and relight
python lav_paint.py --config "configs/relight_inpaint/car.yaml"
```

## 🚝 More Video Diffusion Model Support

Light-A-Video now supports Wan2.1 backbone, a leading DiT-based video foundation model.
Longer video relighting and diverse resolutions are enabled.

### Update Diffusers from source
```bash
conda activate lav

git clone https://github.com/huggingface/diffusers.git
cd diffusers
pip install .
```

### Perform video relighting with Wan2.1
Wan2.1 with Flow-Matching scheduler.
The VDM checkpoint is [Wan2.1-T2V-1.3B-Diffusers](https://huggingface.co/Wan-AI/Wan2.1-T2V-1.3B-Diffusers) and it will be downloaded automatically.
```bash
python lav_wan_relight.py --config "configs/wan_relight/bear.yaml"
```
### Perform video relighting with CogVideoX
CogVideoX with DDIM scheduler.
The VDM checkpoint is [THUDM/CogVideoX-2b](https://huggingface.co/THUDM/CogVideoX-2b) and it will be downloaded automatically.
```bash
python lav_cog_relight.py --config "configs/cog_relight/bear.yaml"
```

## 📎 Citation 

If you find our work helpful for your research, please consider giving a star ⭐ and citation 📝 
```bibtex
@InProceedings{Zhou_2025_ICCV,
    author    = {Zhou, Yujie and Bu, Jiazi and Ling, Pengyang and Zhang, Pan and Wu, Tong and Huang, Qidong and Li, Jinsong and Dong, Xiaoyi and Zang, Yuhang and Cao, Yuhang and Rao, Anyi and Wang, Jiaqi and Niu, Li},
    title     = {Light-A-Video: Training-free Video Relighting via Progressive Light Fusion},
    booktitle = {Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)},
    month     = {October},
    year      = {2025},
    pages     = {13315-13325}
}
```

## 📣 Disclaimer

This is official code of Light-A-Video.
All the copyrights of the demo images and audio are from community users. 
Feel free to contact us if you would like remove them.

## 💞 Acknowledgements
The code is built upon the below repositories, we thank all the contributors for open-sourcing.
* [IC-Light](https://github.com/lllyasviel/IC-Light)
* [AnimateDiff](https://github.com/guoyww/AnimateDiff)
* [CogVideoX](https://github.com/THUDM/CogVideo)
* [Wan2.1](https://github.com/Wan-Video/Wan2.1)

It is greatly appreciated that the community has contributed various extensions to Light-A-Video.
* [ComfyUI_Light_A_Video](https://github.com/smthemex/ComfyUI_Light_A_Video)
