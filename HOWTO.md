
https://hexdocs.pm/nerves/customizing-systems.html

```bash
git remote add upstream git@github.com:nerves-project/nerves_system_x86_64.git
git fetch --tags upstream
git checkout tags/v1.20.3
git checkout -b mice

#update mix.exs metadata

mix deps.get
mix local.nerves
mix nerves.system.shell

make linux-menuconfig
CONFIG_INPUT_MOUSEDEV
CONFIG_INPUT_MISC
CONFIG_INPUT_UINPUT
make linux-update-defconfig

make
exit
#create precompiled artifact
mix nerves.artifact
mv *.tar.gz ~/.nerves/dl
```
