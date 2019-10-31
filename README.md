# KWS_compile_install (Windows)

[安裝Git](https://git-scm.com/)

```
git clone https://github.com/recklight/KWS_compile_install.git
```

## To Use:


1. 使用Anaconda建立py2.7環境
```
conda create --name kws_env python=2.7 anaconda
activate kws_env
```


2. 安裝缺少的package
```
pip install mbed-cli
pip install mercurial
pip install paramiko
pip install jsonschema
pip install pyelftools
```


3. 解壓縮 ML-KWS-for-MCU.rar，得到資料夾 ML-KWS-for-MCU-master；解壓縮CMSIS_5.rar 到 "/ML-KWS-for-MCU-master/Deployment" 中
```
rar x ML-KWS-for-MCU.rar /
rar x CMSIS_5.rar /ML-KWS-for-MCU/Deployment
```


4. 將當前目錄移至
```
cd /ML-KWS-for-MCU/Deployment/kws_realtime_test
mbed deploy
```


5. 複製mbed_libs資料夾下所有.lib 至當前目錄
```
cp ../Examples/realtime_test/mbed_libs/*.lib /
mbed deploy
```


6. [安裝"gcc-arm-none-eabi-6-2017-q2-update-win32-sha2.exe"](https://developer.arm.com/-/media/Files/downloads/gnu-rm/6-2017q2/gcc-arm-none-eabi-6-2017-q2-update-win32-sha2.exe?revision=419232c3-aefe-4049-a88a-7b4ea055ebc7?product=GNU-RM%20Downloads,32-bit,,Windows,6-2017-q2-update)


7. 設定 GCC_ARM_PATH & compile
```
mbed config -G GCC_ARM_PATH "C:\Program Files (x86)\GNU Tools ARM Embedded\6 2017-q2-update\bin"

mbed compile -m DISCO_F746NG -t GCC_ARM --source . --source ../Source --source ../Examples/realtime_test --source ../CMSIS_5/CMSIS/NN/Include --source ../CMSIS_5/CMSIS/NN/Source --source ../CMSIS_5/CMSIS/DSP/Include --source ../CMSIS_5/CMSIS/DSP/Source --source ../CMSIS_5/CMSIS/Core/Include --profile ../release_O3.json -j 8

```


8. 以上步驟中如果有跳出未安裝的package，使用pip(conda) install安裝


9. 將位於"/ML-KWS-for-MCU/Deployment/kws_realtime_test/BUILD/DISCO_F746NG/GCC_ARM-RELEASE_O3G/kws_realtime_test.bin" 拉到板子，完成


