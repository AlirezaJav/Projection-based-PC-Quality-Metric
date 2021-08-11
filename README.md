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
Note that path to PCs is set inside the config file, they are brought to command line arguments to make it easier to run metric for a batch of PCs.
If you want to save point clouds, <b>savePCs</b> should be set to 1 (savePCs = 1)
If you want to save projected images, <b>saveImages</b> should be set to 1 (saveImages = 1). All images of the PC should be stored in a separate folder. The path to this folder is set inside the configuration file.

<p>This Repository will contain the source code of the metric proposed in:</p>
A.Javaheri, C. Brites, F. Pereira, J. Ascenso "Joint Geometry and Color Projection-based Point Cloud Quality Metric" <b>submitted to</b> <i>IEEE Transactions on Multimedia</i>.
