
<div align="right">
  <details>
    <summary >🌐 Language</summary>
    <div>
      <div align="center">
        <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=en">English</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=zh-CN">简体中文</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=zh-TW">繁體中文</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=ja">日本語</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=ko">한국어</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=hi">हिन्दी</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=th">ไทย</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=fr">Français</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=de">Deutsch</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=es">Español</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=it">Italiano</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=ru">Русский</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=pt">Português</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=nl">Nederlands</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=pl">Polski</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=ar">العربية</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=fa">فارسی</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=tr">Türkçe</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=vi">Tiếng Việt</a>
        | <a href="https://openaitx.github.io/view.html?user=bytedance&project=ATI&lang=id">Bahasa Indonesia</a>
      </div>
    </div>
  </details>
</div>

# ATI: Any Trajectory Instruction for Controllable Video Generation

<div align="center">
  
[![arXiv](https://img.shields.io/badge/arXiv%20paper-2505.22944-b31b1b.svg)](https://arxiv.org/pdf/2505.22944)&nbsp;
[![project page](https://img.shields.io/badge/Project_page-ATI-green)](https://anytraj.github.io/)&nbsp;
<a href="https://huggingface.co/bytedance-research/ATI/"><img src="https://img.shields.io/static/v1?label=%F0%9F%A4%97%20Hugging%20Face&message=Model&color=orange"></a>
</div>


> [**ATI: Any Trajectory Instruction for Controllable Video Generation**](https://anytraj.github.io/)<br>
> [Angtian Wang](https://angtianwang.github.io/), [Haibin Huang](https://brotherhuang.github.io/), Jacob Zhiyuan Fang, [Yiding Yang](https://ihollywhy.github.io/), [Chongyang Ma](http://www.chongyangma.com/)
> <br>Intelligent Creation Team, ByteDance<br>

**Highlight: ATI motion transfer tools + demo is added. Scroll down to see the updates**

[![Watch the video](assets/thumbnail.jpg)](https://youtu.be/76jjPT0f8Hs)

This is the repo for Wan2.1 ATI (Any Trajectory Instruction for Controllable Video Generation), a trajectory-based motion control framework that unifies object, local and camera movements in video generation. This repo is based on [Wan2.1 offical implementation](https://github.com/Wan-Video/Wan2.1).

Compared with the original Wan2.1. We add the following files:
- wan/modules/motion_patch.py          | Trajectory instruction kernal module
- wan/utils/motion.py                  | Inference dataloader utils
- tools/plot_user_inputs.py            | Visualizer for user input trajectory
- tools/visualize_trajectory.py        | Visualizer for generated video
- tools/trajectory_editor/             | Interactive trajectory editor
- tools/get_track_from_videos.py       | Motion extraction tools for ATI motion transfer 
- examples/                            | Test examples
- run_example.sh                       | Easy launch script

We modified the following files:
- wan/image2video.py                   | Add blocks to load and parse trajectory  #L256
- wan/configs/__init__.py              | Config the ATI etc.
- generate.py                          | Add an entry to load yaml format inference examples

## Community Works
### ComfyUI
Thanks for Kijai develop the ComfyUI nodes for ATI:
[https://github.com/kijai/ComfyUI-WanVideoWrapper](https://github.com/kijai/ComfyUI-WanVideoWrapper)

FP8 quant Huggingface Model: [https://huggingface.co/Kijai/WanVideo_comfy/blob/main/Wan2_1-I2V-ATI-14B_fp8_e4m3fn.safetensors](https://huggingface.co/Kijai/WanVideo_comfy/blob/main/Wan2_1-I2V-ATI-14B_fp8_e4m3fn.safetensors)

### Guideline
Guideline by Benji: [https://www.youtube.com/watch?v=UM35z2L1XbI](https://www.youtube.com/watch?v=UM35z2L1XbI)

## Install

ATI requires a same environment as offical Wan 2.1. Follow the instruction of INSTALL.md (Wan2.1).

```
git clone https://github.com/bytedance/ATI.git
cd ATI
```

Install packages

```
pip install .
```

First you need to download the 14B original model of Wan2.1.

```
huggingface-cli download Wan-AI/Wan2.1-I2V-14B-480P --local-dir ./Wan2.1-I2V-14B-480P
```

Then download ATI-Wan model from our huggingface repo.

```
huggingface-cli download bytedance-research/ATI --local-dir ./Wan2.1-ATI-14B-480P
```

Finally, copy VAE, T5 and other misc checkpoint from origin Wan2.1 folder to ATI checkpoint location

```
cp ./Wan2.1-I2V-14B-480P/Wan2.1_VAE.pth ./Wan2.1-ATI-14B-480P/
cp ./Wan2.1-I2V-14B-480P/models_t5_umt5-xxl-enc-bf16.pth ./Wan2.1-ATI-14B-480P/
cp ./Wan2.1-I2V-14B-480P/models_clip_open-clip-xlm-roberta-large-vit-huge-14.pth ./Wan2.1-ATI-14B-480P/
cp -r ./Wan2.1-I2V-14B-480P/xlm-roberta-large ./Wan2.1-ATI-14B-480P/
cp -r ./Wan2.1-I2V-14B-480P/google ./Wan2.1-ATI-14B-480P/
```

## Run

We provide a demo sript to run ATI.

```
bash run_example.sh -p examples/test.yaml -c ./Wan2.1-ATI-14B-480P -o samples
```
where `-p` is the path to the config file, `-c` is the path to the checkpoint, `-o` is the path to the output directory, `-g` defines the number of gpus to use (if unspecificed, all avalible GPUs will be used; if `1` is given, will run on single process mode).

Once finished, you will expect to fine:
- `samples/outputs` for the raw output videos.
- `samples/images_tracks` shows the input image togather with the user specified trajectories.
- `samples/outputs_vis` shows the output videos togather with the user specified trajectories.

Expected results:


<table style="width: 100%; border-collapse: collapse; text-align: center; border: 1px solid #ccc;">
  <tr>
    <th style="text-align: center;">
      <strong>Input Image & Trajectory</strong>
    </th>
    <th style="text-align: center;">
      <strong>Generated Videos (Superimposed Trajectories)</strong>
    </th>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/00.jpg" alt="Image 0" style="height: 240px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/00.gif" alt="Image 0" style="height: 240px;">
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/01.jpg" alt="Image 1" style="height: 240px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/01.gif" alt="Image 1" style="height: 240px;">
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/02.jpg" alt="Image 2" style="height: 160px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/02.gif" alt="Image 2" style="height: 160px;">
    </td>
  </tr>

  </tr>
  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/03.jpg" alt="Image 3" style="height: 220px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/03.gif" alt="Image 3" style="height: 220px;">
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/04.jpg" alt="Image 4" style="height: 240px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/04.gif" alt="Image 4" style="height: 240px;">
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/05.jpg" alt="Image 5" style="height: 160px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/05.gif" alt="Image 5" style="height: 160px;">
    </td>
  </tr>
</table>

## Motion Transfer

![Motion Transfer](assets/MotionTransfer.jpg)
ATI can mimic a video by extracting its motion dynamics along with its first-frame image. Moreover, by leveraging powerful image-editing tools, it also enables "video-editing" capabilities.

First, extract motions from videos using the following script:
```
python3 tools/get_track_from_videos.py --source_folder examples/motion_transfer/ --save_folder samples_motion_transfer/
```

Then run ATI inference
```
bash run_example.sh -p samples_motion_transfer/test.yaml -c ./Wan2.1-ATI-14B-480P -o outputs_motion_transfer
```

Expected result

<table style="width: 100%; border-collapse: collapse; text-align: center; border: 1px solid #ccc;">
  <tr>
    <th style="text-align: center;">
      <strong>Reference Video (for Extracting Motion)</strong>
    </th>
    <th style="text-align: center;">
      <strong>First Frame Image</strong>
    </th>
    <th style="text-align: center;">
      <strong>Generated Video</strong>
    </th>
  </tr>


  <tr>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/RV_0.gif" alt="Motion Transfer Video" style="height: 160px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/RI_0.png" alt="Motion Transfer Image" style="height: 160px;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <img src="assets/examples/G_0.gif" alt="Motion Transfer Output" style="height: 160px;">
    </td>
  </tr>
</table>


## Create You Own Trajectory

We provide an interactive tool that allow users to draw and edit trajectories on their images. 
Important note: **app.py** should only be run on **localhost**, as running it on a remote server may pose security risks.

1. First run:
```
cd tools/trajectory_editor
python3 app.py
```
then open this url [localhost:5000](http://localhost:5000/) in the browser. 

2. Get the interface shown below, then click **Choose File** to open a local image.  
![Interface Screenshot](assets/editor0.PNG)

3. Available trajectory functions:  
![Trajectory Functions](assets/editor1.PNG)

   a. **Free Trajectory**: Click and then drag with the mouse directly on the image.  
   b. **Circular (Camera Control)**:  
      - Place a circle on the image, then drag to set its size for frame 0.  
      - Place a few (3–4 recommended) track points on the circle.  
      - Drag the radius control to achieve zoom-in/zoom-out effects.  

   c. **Static Point**: A point that remains stationary over time.  

   *Note:* Pay attention to the progress bar in the box to control motion speed.  
   ![Progress Control](assets/editor2.PNG)

4. **Trajectory Editing**: Select a trajectory here, then delete, edit, or copy it. In edit mode, drag the trajectory directly on the image. The selected trajectory is highlighted by color.  
![Trajectory Editing](assets/editor3.PNG)

5. **Camera Pan Control**: Enter horizontal (X) or vertical (Y) speed (pixels per frame). Positive X moves right; negative X moves left. Positive Y moves down; negative Y moves up. Click **Add to Selected** to apply to the current trajectory, or **Add to All** to apply to all trajectories. The selected points will gain a constant pan motion on top of their existing movement.  
![Camera Pan Control](assets/editor4.PNG)

6. **Important:** After editing, click **Store Tracks** to save. Each image (not each trajectory) must be saved separately after drawing all trajectories.  
![Store Tracks](assets/editor5.PNG)

7. Once all edits are complete, locate the `videos_example` folder in the **Trajectory Editor**.


## Citation
Please cite our paper if you find our work useful:
```
@article{wang2025ati,
  title={{ATI}: Any Trajectory Instruction for Controllable Video Generation},
  author={Wang, Angtian and Huang, Haibin and Fang, Zhiyuan and Yang, Yiding, and Ma, Chongyang}
  journal={arXiv preprint},
  volume={arXiv:2505.22944},
  year={2025}
}
```

