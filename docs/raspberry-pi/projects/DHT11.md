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

## 问题排查

### `lgpio安装失败`的解决方案


#### `swig`模块不存在

错误日志1:
```bash
Rpi-lgpio installation error code:
Building wheels for collected packages: lgpio
Building wheel for lgpio (pyproject.toml) ... error
error: subprocess-exited-with-error

× Building wheel for lgpio (pyproject.toml) did not run successfully.
│ exit code: 1
╰─> [8 lines of output]
running bdist_wheel
running build
running build_py
running build_ext
building '_lgpio' extension
swigging lgpio.i to lgpio_wrap.c
swig -python -o lgpio_wrap.c lgpio.i
error: command 'swig' failed: No such file or directory
[end of output]

note: This error originates from a subprocess, and is likely not a problem with pip.
ERROR: Failed building wheel for lgpio
Failed to build lgpio
ERROR: Failed to build installable wheels for some pyproject.toml based projects (lgpio)
```

解决方案：

+ 全局安装`swig`工具
```bash
sudo update
sudo apt install swig
swig --version
```

### 虚拟环境中的`lgpio`安装失败

错误日志2:
```bash
× Building wheel for lgpio (pyproject.toml) did not run successfully.
│ exit code: 1
╰─> [14 lines of output]
    running bdist_wheel
    running build
    running build_py
    running build_ext
    building '_lgpio' extension
    swigging lgpio.i to lgpio_wrap.c
    swig -python -o lgpio_wrap.c lgpio.i
    creating build/temp.linux-aarch64-cpython-313
    aarch64-linux-gnu-gcc -I/usr/include -fPIC -Isrc -I/home/liuranshen/embedded_raspi/projects/dht11/dht11_venv/include -I/usr/include/py
on3.13 -c lgpio_wrap.c -o build/temp.linux-aarch64-cpython-313/lgpio_wrap.o
    creating build/lib.linux-aarch64-cpython-313
    aarch64-linux-gnu-gcc -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-z,relro -g -fwrapv -O2 -L/usr/lib/aarch64-linux-gnu -I/usr/include
uild/temp.linux-aarch64-cpython-313/lgpio_wrap.o -L/usr/lib/aarch64-linux-gnu -llgpio -o build/lib.linux-aarch64-cpython-313/_lgpio.cpytho
313-aarch64-linux-gnu.so
    /usr/bin/ld: cannot find -llgpio: No such file or directory
    collect2: error: ld returned 1 exit status
    error: command '/usr/bin/aarch64-linux-gnu-gcc' failed with exit code 1
    [end of output]

note: This error originates from a subprocess, and is likely not a problem with pip.
ERROR: Failed building wheel for lgpio
iled to build lgpio
ror: failed-wheel-build-for-install

Failed to build installable wheels for some pyproject.toml based projects
> lgpio

```

解决方法:

+ 错误出在构建时，缺少`libgpio.os`软连接，当查找`libgpio.os`软链接时，出现下列情况则意味着缺少软链接:
```bash
(dht11_venv) liuranshen@liuranrasp:~/embedded_raspi/projects/dht11 $ find /usr/lib/aarch64-linux-gnu/ -type f -name "liblgpio*"
/usr/lib/aarch64-linux-gnu/liblgpio.so.1
```

+ 需手动创建软链接:
```bash
# 进入库文件目录
cd /usr/lib/aarch64-linux-gnu/

# 创建软链接（-s 表示软链接，liblgpio.so 指向已存在的 liblgpio.so.1）
sudo ln -s liblgpio.so.1 liblgpio.so

# 验证软链接是否创建成功
ls -l liblgpio*
```

+ PS: 可以手动指定`pip`安装编译时的参数:
```bash
CFLAGS="-I/usr/include" LDFLAGS="-L/usr/lib/aarch64-linux-gnu" pip install lgpio --force-reinstall --no-cache-dir
```

## 当前仍然存在问题

[参考文档](https://github.com/adafruit/Adafruit_CircuitPython_DHT/issues/33)
