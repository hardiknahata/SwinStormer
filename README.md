# SwinStormer: High Resolution Image Deraining
We propose a `Novel Deep Learning Architecture` for the Image Deraining task, or in simple words, to remove rain from a single image.

Our architecture is inspired by the fusion of the following approaches:
- `Restormer: Efficient Transformer for High-Resolution Image Restoration`  - https://arxiv.org/pdf/2111.09881.pdf
- `Swin Transformer: Hierarchical Vision Transformer using Shifted Windows`  - https://arxiv.org/pdf/2103.14030

![Network Architecture](model-architecture.png)

## Requirements

```
pip install -r requirements.txt
```

## Dataset

[Rain100L](https://mega.nz/file/MpgnwYDS#jqyDEyL1U9srLBbEFCPnAOZb2HZTsSrwSvRGQ6m6Dzc) and [Rain100H](https://www.dropbox.com/s/kzbzer5wem37byg/rain100H.zip?dl=0) are used, download these datasets and make 
ensure the directory structure looks like this:
```                           
|-- data     
    |-- rain100L
        |-- train
            |-- rain
                norain-1.png
                ...
            `-- norain
                norain-1.png
                ...
        `-- test                                                        
    |-- rain100H
        same as rain100L
```

## Usage

You can easily train and test the model by running the command below. If you want to try other options, please refer to
[utils.py](utils.py).

### Train Model

```
python main.py --data_name rain100L --seed 0
```

### Test Model
Download the model from the link given at the bottom of the ReadMe or train the model before running this command:
```
python main.py --data_name rain100H --model_file result/rain100H.pth
```

## Benchmarks
The models are trained on one NVIDIA Tesla V100 GPU (8GB).

<table>
<thead>
  <tr>
    <th rowspan="3">Method</th>
    <th colspan="2">Rain100L</th>
    <th colspan="2">Rain100H</th>
    <th rowspan="3">Download</th>
  </tr>
  <tr>
    <td align="center">PSNR</td>
    <td align="center">SSIM</td>
    <td align="center">PSNR</td>
    <td align="center">SSIM</td>
  </tr>
</thead>
<tbody>
  <tr>
    <td align="center">SwinStormer</td>
    <td align="center">38.68</td>
    <td align="center">0.981</td>
    <td align="center">29.13</td>
    <td align="center">0.868</td>
    <td align="center"><a href="https://mega.nz/folder/Ph0DyJJL#XTYf0aa0_sQ61-Y4LiiFmQ">Link</a></td>
  </tr>
</tbody>
</table>

## License
This project is licensed under the terms of the GNU General Public License v3.0. You can find a copy of the license in the [LICENSE](LICENSE) file.
