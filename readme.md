## Компиляция под arm

### Дополнительные файлы

```bash
wget https://snapshots.linaro.org/gnu-toolchain/13.0-2022.11-1/arm-linux-gnueabihf/gcc-linaro-13.0.0-2022.11-x86_64_arm-linux-gnueabihf.tar.xz
wget https://snapshots.linaro.org/gnu-toolchain/13.0-2022.11-1/arm-linux-gnueabihf/sysroot-glibc-linaro-2.36.9000-2022.11-arm-linux-gnueabihf.tar.xz
```
Разархивируйте в корне проекта.

### Сборка

```bash
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=./install -DCMAKE_C_COMPILER='../gcc-linaro-13.0.0-2022.11-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-gcc' -DCMAKE_CXX_COMPILER='../gcc-linaro-13.0.0-2022.11-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-g++' ..
make -j4
make install
```

### Тестирование

```bash
qemu-arm -L ../sysroot-glibc-linaro-2.36.9000-2022.11-arm-linux-gnueabihf/libc install/bin/MainLib
# Possible output: "Variable"
```
