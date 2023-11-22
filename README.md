# ultralytics_mlu
ultralytics for cambricon mlu.

## Environment
1. Install cambricon driver:
```
wget https://sdk.cambricon.com/static/Driver/MLU370_v5.10.22_X86_ubuntu20.04_dpkg/cambricon-mlu-driver-ubuntu20.04-dkms_5.10.22_amd64.deb
dpkg-query -s dkms
dpkg-query -s gcc
dpkg-query -s linux-headers-$(uname -r)
sudo dpkg -i <package.deb>
```
use ```cnmon``` to test.

2. Install CNToolkit,Cambricon CNNL,CNCL,CNCV,Cambricon DALI,CNNL_Extra,Cambricon BANGC OPS:
```
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cntoolkit_3.7.2-1.ubuntu20.04_amd64.deb
sudo apt install ./cnnl_<x.y.z>-1.ubuntu<a.b>_<arch>.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cnnl_1.21.1-1.ubuntu20.04_amd64.deb
sudo apt install ./cncl_<x.y.z>-1.ubuntu<a.b>_<arch>.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cnnlextra_1.5.0-1.ubuntu20.04_amd64.deb
sudo apt install ./cnnlextra_<x.y.z>-1.ubuntu<a.b>_<arch>.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cncl_1.13.0-1.ubuntu20.04_amd64.deb
sudo apt install ./cncl_<x.y.z>-1.ubuntu<a.b>_<arch>.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cncv_2.3.0-1.ubuntu20.04_amd64.deb
sudo apt install ./cncv_<x.y.z>.ubuntu<a.b>_<arch>.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/mluops_0.9.0-1.ubuntu20.04_amd64.deb
sudo dpkg -i mluops_0.9.0-1.ubuntu18.04_amd64.deb
wget https://sdk.cambricon.com/static/Basis/MLU370_X86_ubuntu20.04/cambricon_dali-0.9.0-py3-none-manylinux2014_x86_64.whl
pip install cambricon_dali-0.9.0-py3-none-manylinux2014_x86_64.whl
```
3. Set environment path:
```
export NEUWARE_HOME=usr/local/neuware # 依赖库安装路径，根据依赖库实际安装路径修改
export PATH=$PATH:$NEUWARE_HOME/bin # 系统环境变量，添加依赖库可行执行文件路径
export LD_LIBRARY_PATH=$NEUWARE_HOME/lib64:$LD_LIBRARY_PATH # 系统环境变量， 添加依赖库库文件路径
```

4. Install Cambricon PyTorch,torch_mlu and torchvision, remember Cambricon PyTorch 1.13 only support Python 3.10 now.
```
wget https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torch-1.13.1-cp310-cp310-linux_x86_64.whl
wget https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torch_mlu-1.17.0+torch1.13-cp310-cp310-linux_x86_64.whl
wget https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torchvision-0.14.1a0+5e8e2f1-cp310-cp310-linux_x86_64.whl
pip install https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torch-1.13.1-cp310-cp310-linux_x86_64.whl
pip install https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torch_mlu-1.17.0+torch1.13-cp310-cp310-linux_x86_64.whl
pip install https://sdk.cambricon.com/static/PyTorch/MLU370_1.13_v1.17.0_X86_ubuntu18.04_python3.10_pip/torchvision-0.14.1a0+5e8e2f1-cp310-cp310-linux_x86_64.whl
```
5. Install ultralytics
```
git clone https://github.com/cf206cd/ultralytics_mlu.git
cd ultralytics_mlu
pip install -e .
```
## Usage
Same as https://github.com/ultralytics/ultralytics.