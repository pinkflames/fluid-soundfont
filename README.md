# The Fluid R3 soundfont
This repository preserves the Fluid R3 soundfont by Frank Wen as it was
shipped by Debian/Ubuntu and Gentoo Linux.

There exist updated versions from [MuseScore](https://musescore.org) but these,
I believe, are the originals that have been extracted from Gentoo's
fluid-soundfont_3.1.tar.gz and verified via checksumming to be identical to the
fluid-soundfont_3.1.orig.tar.gz ,
[provided by the Debian project](https://packages.debian.org/sid/fluid-soundfont-gm)
and [recorded by Toby Smithe of Ubuntu](https://metadata.ftp-master.debian.org/changelogs//main/f/fluid-soundfont/fluid-soundfont_3.1-5.2_copyright)
as originating from `http://www.musescore.org/download/fluid-soundfont.tar.gz` on Fri, 08 Feb 2008 00:08:09 +0000.

## Why is this using a weird file extension?
Unfortunately GitHub does not support files over 100 MiB in size, and the Large
File Storage has a meager 1 GiB bandwidth limit. The only way for this to be
available to a large number of people, if it gets accepted as a valid source
of the original Fluid R3 soundfont, is a bit of trickery that I learned about
while investigating Debian packaging - we shoehorn the data into FLAC:

`flac --endian=little --channels=1 --bps=16 --sample-rate=44100 --sign=signed FluidR3_GM.sf2 -o FluidR3_GM.sf2.flacy`

## How to undo the FLACy weirdness
All one needs to undo it is to decompress it with the flac tool, taking care to
force use of raw output (since the original data wasn't uncompressed audio):

`flac --force-raw-format --endian=little --sign=signed -d FluidR3_GM.sf2.flacy -o FluidR3_GM.sf2`

## SHA-512 checksums
|Filename                       |Size in bytes|SHA-512|Description|
|:-----------------------------:|------------:|:-----:|:---------:|
|fluid-soundfont_3.1.orig.tar.gz|    134835922|014394752ac50d3162c87903d9dd6b38d199ddfab10e2dea3b2a96d02ddcb876a792cc20bc0e83be5ac15eb0c7e261612eedcd792a3f0ff85a7d032a7dd24f29|Original source file from Debian/Ubuntu|
|fluid-soundfont_3.1.tar.gz     |    134835922|014394752ac50d3162c87903d9dd6b38d199ddfab10e2dea3b2a96d02ddcb876a792cc20bc0e83be5ac15eb0c7e261612eedcd792a3f0ff85a7d032a7dd24f29|Gentoo's version obtained from `http://prereleases.musescore.org/soundfont/fluid-soundfont_3.1.tar.gz`|
|COPYING                        |         1086|b02479e5af2cdc25dbf3f5f1057b58b1468ce8218cd76e575252e72c8be7dea1dcee1b60ce60f0516b9cf3c467901631ee80b2df844acddc3c3a0b16df578248|19 feb  2008|
|FluidR3_GM.sf2                 |    148398306|023cca1683ae18376999ae8121fbfbd134f345b6539e32b2eaa91929e23695785798e9983aaa1bb1e2c88587c8d5b172e4a041b505fff3fbd8bd17314cb8c4e3|24 feb  2008|
|FluidR3_GS.sf2                 |      3201926|7b09d1a3741528c8dab77d74ecd424325c4db9e32b9a8a3a1b018f600aee871d0c6e56b3b098ee58312b40809c78d3e85876d42e1f5c7d5f10857ebae5ad6967|24 feb  2008|
|README                         |         1042|edb743176462a4e48456421c40a065d58ba04576b087969304956f49a3045a6812d2b7d5802ffc69ef800406b481268d0d61bbcf49322dc0ba61d77ed7121f5f|20 feb  2008|
|FluidR3_GM.sf2.flacy |    77007900|3233ea80c40410bbe1318c1a08e993821dd9d8ebc4fdd5449e117c61dcb288b2ba28552312537ee8cb941c451d1935eb4d805aa342f5d139d934dfe9a284acb9|flac compressed GM variant|
|FluidR3_GS.sf2.flacy |     1861104|f24a1e97dff65aa6553913c076a8af17ddb484ff4de8dd5ede036fd9f9bee46d37e87809de4a1ab0423eff6dab82a8a02b56ae04dd4577ed78aab58cca866519|flac compressed GS variant|
|timidity.cfg.bz2     |       10667|def3ba456c040a010e7e5d22eed1e1674f8b50853c5771085a16eced47e9a8e429b34564218df6a4a16f697eda69365afe51a0d158b0672a66fdf1b0284c50f5|TiMidity patchset that shipped with Gentoo and was originally uploaded to `https://dev.gentoo.org/~hwoarang/distfiles/timidity.cfg.bz2` by Gentoo developer [Markos Chandras](https://bugs.gentoo.org/251364)|
|timidity.cfg         |      234909|8e0501813dc5ac3ffd50dcd5993a46e9f33d2cd02bc7b0fe74bb90d7fc5a416aafd5a6ca07ecf967fd389f40d44affc00d11a6aea01870f35ab6c30827bfe15b|Decompressed timidity.cfg.bz2 from Gentoo|
