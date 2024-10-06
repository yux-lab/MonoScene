可以用 pip 来代替 conda 安装依赖

跟着教程创建相应的保存目录
```bash
export KITTI_PREPROCESS=/mnt/data2/monoscene_pre/semantic_kitti/preprocess/folder/
export KITTI_ROOT=/mnt/data/SGN_Dataset/kitti/
export KITTI_LOG=/mnt/data2/monoscene_pre/semantic_kitti/logdir/
export MONOSCENE_OUTPUT=/mnt/data2/monoscene_pre/semantic_kitti/output/
```

```bash
python monoscene/scripts/train_monoscene.py     dataset=kitti     enable_log=true   kitti_root=$KITTI_ROOT     kitti_preprocess_root=$KITTI_PREPROCESS    kitti_logdir=$KITTI_LOG     n_gpus=4 batch_size=4
```



## mayavi 可视化
follow: [GitHub - enthought/mayavi: 3D visualization of scientific data in Python](https://github.com/enthought/mayavi)

### 运行成功是在 bash 而不是 conda，确保环境为 python 3.8，3.10 不支持 numpy==1.19.5

```bash
# 将mayavi拉到本地
git clone https://github.com/enthought/mayavi.git
cd mayavi

# 安装相应环境
pip install PyQt5
pip install vtk
pip install configobj
pip install hydra-core --upgrade
pip install omegaconf
python setup.py install

pip uninstall numpy==1.19.5
pip install numpy==1.19.5

# 运行脚本可视化
python monoscene/scripts/visualization/kitti_vis_pred.py +file=/mnt/data2/monoscene_pre/semantic_kitti/output/kitti/08/000555.pkl +dataset=kitti
```