# Rockchip pack and unpack tool

This project is based on http://gitorious.org/rockchip-android/tools

## Preparetion

build required(libssl-dev for md5 checksum)

	apt-get install git gcc libssl-dev

Get source code & build

	git clone git://github.com/jhonxie/rk2918_tools.git
	cd rk2918_tools
	make

Several executable bins are built

	img_unpack  固件新格式转旧格式
	img_maker	固件旧格式打包成新格式
	afptool		旧格式固件打包解包工具
	mkkrnlimg  pack kernel or ramdisk to add KRNL head and CRC checksum

## Usage(release_update.img is the final package, update.img here is just data):

### Pack

Pack all metadata image into update.img(need parameter)

	afptool -pack . update_data.img

Final pack update_data.img into release update.img

	img_maker -rk33 MiniLoaderAll.bin update_data.img release_update.img

### Unpack

Unpack release_update.img into img directory(loader.img and the real update.img data)

	img_unpack release_update.img img

Unpack the update.img(update data) from above into metadata directory

	cd img
	afptool -unpack update.img metadata

PS: the rkflash tool not implemented in this project, you can find it here: http://forum.xda-developers.com/showthread.php?t=1286305
