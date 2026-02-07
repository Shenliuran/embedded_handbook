# 树莓派DHT11温湿度传感器项目

[参考链接](https://docs.sunfounder.com/projects/umsk/en/latest/05_raspberry_pi/pi_lesson19_dht11.html)

## 项目前期配置

环境
```bash
mkdir dht11
python -m venv dht11_venv
source dht11_venv/bin/activate
pip3 install adafruit-circuitpython-dht
```

+ 在树莓派5中，无法使用pip直接安装三方包，需要先创建虚拟环境，在虚拟环境中安装相应的包。
+ 实验证明，对于`uv`这种第三方的包管理工具，无法让项目正常运行

> [!NOTE]
> DHT11和DHT22设备都需要在数据信号线上加一个上拉电阻。这个电阻的范围是1k到5k

