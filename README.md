# AI

## INSTALL

1. Clone this repository.
```
git clone https://github.com/GamSeong-HwaBaek/AI
```
2. Create new conda environment.
```
conda create -n capstone python=3.8
```

3. Please install PyTorch as latest version with link below, yourself.
https://pytorch.org/

4. Install other dependencies.
```
pip install git+https://git@github.com/SKTBrain/KoBERT.git@master
pip install gluonnlp numpy tqdm pandas
```

5. Download [pretrained model(368MB)](https://drive.google.com/file/d/1n198rKOGaATRHaeSteLQLp9HL4EGxRRw/view?usp=sharing) and move file into `model` folder -> (model/model.pt)

## Recommending 5 Paintings

```
python rec_paintings.py <사용자 선택 감성> <일기 본문>

ex) python rec_paintings.py sleepy 개졸리다개졸리다개졸리다개졸리다개졸리다
```
It will make `paintings.txt` in root folder.
```
./data/image/57727a9bedc2cb3880df19ad.jpg
./data/image/57727651edc2cb3880d1371c.jpg
./data/image/57727daeedc2cb3880e8763d.jpg
./data/image/57728593edc2cb38800191a6.jpg
./data/image/577284e0edc2cb3880ff2caa.jpg
```

## Style Transfer
After choosing one paintings of five, we can use its filename as argument(<선택한 명화 파일명>).
```
python ./neural-style-pt/neural_style.py -style_image <선택한 명화 파일명> -content_image <사용자가 업로드한 사진 파일명> -output_image ./output/result.png -model_file ./neural-style-pt/models/nin_imagenet.pth -gpu 0 -backend cudnn -num_iterations 1000 -seed 123 -content_layers relu0,relu3,relu7,relu12 -style_layers relu0,relu3,relu7,relu12 -content_weight 5 -style_weight 500 -image_size 512 -optimizer adam -save_iter 1 -original_colors 1 

ex) python ./neural-style-pt/neural_style.py -style_image ./data/image/577284e0edc2cb3880ff2caa.jpg -content_image <사용자가 업로드한 사진 파일명> -output_image ./output/result.png -model_file ./neural-style-pt/models/nin_imagenet.pth -gpu 0 -backend cudnn -num_iterations 1000 -seed 123 -content_layers relu0,relu3,relu7,relu12 -style_layers relu0,relu3,relu7,relu12 -content_weight 5 -style_weight 500 -image_size 512 -optimizer adam -save_iter 1 -original_colors 1 
```

It will save result in `output` folder.
