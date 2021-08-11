# Projection-based-PC-Quality-Metric
<b>Introduction</b>
<p>A novel joint geometry and color projection-based point cloud objective quality metric which solves the critical weakness of this type of quality metrics, i.e., the misalignment between the reference and degraded projected images. Moreover, this point cloud quality metric exploits the best performing 2D quality metrics in the literature to assess the quality of the projected images.</p>
<b>Installation Instructions</b>
<p>Image Quality Assessment (<a href="https://pypi.org/project/IQA-pytorch/">IQA</a>) Models in PyTorch should be installed</p>

```console
pip install IQA_pytorch
```
<a href="http://www.open3d.org/docs/release/getting_started.html">Open3d</a> python packages are also necessary to read/write point clouds.

```console
pip install open3d
```
Conda instalation

```console
conda install -c open3d-admin -c conda-forge open3d
```
<a href="https://pypi.org/project/opencv-python/">OpenCV</a> is also necessary for image processing operations in the metric.

```console
pip install opencv-python
```
You need to also install <a href="https://numpy.org/">Numpy</a>, <a href="https://pandas.pydata.org/">Pandas</a>, and <a href="https://pytorch.org/">PyTorch</a> (in case that you want to run 2D metrics on GPU)

<b>Usage</b>
<p>All metric parameters should be set inside the configuration file (config.ini) before running the metric. If it is the first time runing the metric and recolored point clouds are not available:</p>

```console
python3 compute_projqm -a reference PC -b degraded PC -c config.ini -o output.csv
```
<p>Note that path to PCs is set inside the config file, they are brought to command line arguments to make it easier to run metric for a batch of PCs.</p>
<p>If you want to save point clouds, <b>savePCs</b> should be set to 1 (savePCs = 1) </p>
<p>If you want to save projected images, <b>saveImages</b> should be set to 1 (saveImages = 1). All images of the PC should be stored in a separate folder. The path to this folder is set inside the configuration file.</p>
<p>Precision of the input point clouds should also be set in the configuration file.</p>
<p>There is also a flag for each of the 2D quality metrics that you want to be included in the final results<p>
<p> You can see a sample configuration file below: </p>

```console
[Paths]
# Path to directory including reference point clouds
PCA = C:\AlirezaJav\Datasets\EPFL_MPEG_Codecs\stimuli\  
# Path to directory including reference point clouds                           
PCB = C:\AlirezaJav\Datasets\EPFL_MPEG_Codecs\stimuli\	
# Path to directory including recolored reference point clouds                         
PCA_rec = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\Recolored PCs\
# Path to directory including recolroed degraded point clouds 
PCB_rec = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\Recolored PCs\
# Path to directory including six projected images of the reference point cloud (All six projected images of a point cloud should be in a folder)
RefImages = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\RefImages\
# Path to directory including six projected images of the degraded point cloud (All six projected images of a point cloud should be in a folder)
DegImages = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\DegImages\
# Path to directory including six projected images of the recolored reference point cloud (All six projected images of a point cloud should be in a folder)
RefImages_rec = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\RecoloredRefImages\
# Path to directory including six projected images of the recolored degraded point cloud (All six projected images of a point cloud should be in a folder)
DegImages_rec = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\RecoloredDegImages\
# Path to directory including six occupancy maps of the reference point cloud (All six occupancy maps of a point cloud should be in a folder)
RefOMs = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\RefOMs\
# Path to directory including six occupancy maps of the degraded point cloud (All six occupancy maps of a point cloud should be in a folder)
DegOMs = C:\AlirezaJav\Projects\Projection-based Metric\Final Software\DegOms\

[Flags]
# Set to 1 if projected images are available and there is no need for projection, 0 otherwise
projected = 0
# Set to 1 if recolored point clouds are saved before and there is no need for recoloring, 0 otherwise
Recolored = 0
# Set to 1 to save recolored point clouds for further use
savePCs = 1
# Set to 1 to save projected images after pre-processing, otherwise 0 (they can be evaluate directly by 2D metric later)
saveImages = 1


[parameters]
# precision of the input PC
precision = 10
# window search size for filtering points after projection. Put zero if you don't want filtering (W = 2*window size + 1)
window size = 2

[2D Metrics]
# compute DISTS
dists = 1
# compute LPIPS
lpips = 1
# compute FSIM
fsim = 1
# compute VSI
vsi = 1
# compute HaarPSI
haarpsi = 1
# compute VIFp
vifp = 1
# compute SSIM
ssim = 1
# compute MS-SSIM
ms-ssim = 1
# compute HVS PSNR and HVS PSNR M
psnr-hvs = 1
# compute PSNR
psnr = 1
```

<p>This Repository will contain the source code of the metric proposed in:</p>
A.Javaheri, C. Brites, F. Pereira, J. Ascenso "Joint Geometry and Color Projection-based Point Cloud Quality Metric" <b>submitted to</b> <i>IEEE Transactions on Multimedia</i>.
