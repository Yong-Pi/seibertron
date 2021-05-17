# 环境准备

环境: 注意esp32的构建需要用到python2.7和pip2.7
`$ pip install future serial pyserial`
工具链:esp32需要使用到的工具链是`xtensa-esp32-elf` 截止目前，该工具的安装仍然需要手动部署，而没有集成到zephyr-sdk。下面是两种安装方式：

## 自动安装

`$ west espressif install`
国内由于网络环境的差异,自动安装经常会遇到连不上的情况,推荐使用手动安装

## 手动安装

Release下载地址:https://github.com/espressif/crosstool-NG/releases
选择合适的平台, 一般为:xtensa-esp32-elf-gcc8_4_0-esp-2020r3-linux-amd64.tar.gz
下载解压到`${HOME}/zephyr-sdk/xtensa/xtensa-esp32-elf`

### 环境配置

`$ export ZEPHYR_TOOLCHAIN_VARIANT="espressif"`
`$ export ESPRESSIF_TOOLCHAIN_PATH="${HOME}/zephyr-sdk/xtensa/xtensa-esp32-elf"`
`$ export PATH=$PATH:$ESPRESSIF_TOOLCHAIN_PATH/bin`

## 获取esp32的开发库

`$ west espressif update`

# 构建
`$ west build -b esp32 -s zephyr/samples/hello_world/`


# 参考地址

zephyr doc: https://docs.zephyrproject.org/latest/boards/xtensa/esp32/doc/index.html

zephyr doc: https://docs.espressif.com/projects/esp-idf/en/v4.2/esp32/api-guides/tools/idf-tools.html#xtensa-esp32-elf
