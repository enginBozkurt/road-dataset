# Download and pre-process ROAD dataset

Here, we release the download instructions and pre-processing instructions for ROAD dataset. It is released with a [paper](#) and [3D-RetinaNet](https://github.com/gurkirt/3D-ReintaNet) as baseline code. Which also contains evaluation code.

## Main Features

- Action annotations for human as well as other road agents, e.g. Turning-right, Moving-away etc. 
- Agent type labels, e.g. Pedestrian, Car, Cyclist, Large-Vehicle, Emergency-Vehicle etc.
- Semantic location labels of the location of agent, e.g. in vehicle lane, in right pavement etc.
- 122K frames from 22 videos annotated, each video is 8 mins long on an average.
- track/tube id annotated for every bounding box on every frame for every agent in the scene.
- 7K tubes/tracks of individual agents.
    - Each tube consists  on  average  of  approximately  80  bounding  boxes linked  over  time.
- 559K bounding  box-level agent  labels.
- 641K and 498K bounding box-level action and location labels.
- 122k annotated with self/ego-actions of AV as well, e.g. AV-on-the-mov, AV-Stopped, AV-turning-right, AV-Overtaking etc.

## Attribution
ROAD dataset is build upon [Oxford Robot Car Dataset (OxRD)](https://robotcar-dataset.robots.ox.ac.uk/about/). Please cite the original dataset if it useful in your work, citation can be found [here](https://robotcar-dataset.robots.ox.ac.uk/citation/). 

Similar to original work, this work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0](http://creativecommons.org/licenses/by-nc-sa/4.0) International License and is intended for non-commercial academic use. If you are interested in using the dataset for commercial purposes please contact original creator [OxRD](https://robotcar-dataset.robots.ox.ac.uk/contact/) for video content and [Fabio](https://cms.brookes.ac.uk/staff/FabioCuzzolin/) and [Gurkirt](http://gurkirt.github.io/) for event annotations.

## Download
We release annotations annotated by [Visual Artificial Intelligence Laboratory](https://cms.brookes.ac.uk/staff/FabioCuzzolin/) and  the pre-processed videos from [OxRD](https://robotcar-dataset.robots.ox.ac.uk/about/). Pre-processing includes `demosaic` for RGB conversion, `ffmpeg` for `.mp4` conversion and fixing the frame-rate. More details can be found in [tar2mp4](./tar2mp4/README.md).

You can download the `Train-Val-set` videos and annotation from [Google-Drive link](https://drive.google.com/drive/folders/1hCLlgRqsJBONHgwGPvVu8VWXxlyYKCq-?usp=sharing)

Private video of `Test-set` will be released in accordance with the challenge.

## Frame-extraction

Baseline code for [3D-RetinaNet](https://github.com/gurkirt/3D-ReintaNet) used in dataset release [paper](#) uses sequences of frames as input. Once you have downloaded the videos from Google-Drive, create a folder name `road` and put annotation under it, create another folder name `videos` under it, put all the videos under a folder name `videos`. Now, your folder structure looks like following:

```
    road/
        - road_trainval_v1.0.json
        - videos/
            - 2014-06-25-16-45-34_stereo_centre_02
            - 2014-06-26-09-53-12_stereo_centre_02
            - ........

```

Now, you can use `extract_videos2jpgs.py` to extract frames. Provide path to `road` folder as argument. You will ffmpeg install on your system or with python.

```
python extract_videos2jpgs.py <path-to-road-folder>/road/
```

Now, the `road` directory would look like.

```
    road/
        - road_trainval_v1.0.json
        - videos/
            - 2014-06-25-16-45-34_stereo_centre_02
            - 2014-06-26-09-53-12_stereo_centre_02
            - ........
        - rgb-images
            - 2014-06-25-16-45-34_stereo_centre_02/
                - 00001.jpg
                - 00002.jpg
                - .........*.jpg
            - 2014-06-26-09-53-12_stereo_centre_02
                - 00001.jpg
                - 00002.jpg
                - .........*.jpg
            - ......../
                - ........*.jpg

```

After this you are ready to train or test [3D-RetinaNet](https://github.com/gurkirt/3D-ReintaNet).