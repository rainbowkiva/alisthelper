# alisthelper

说明：AListHelper是为AList提供GUI界面的开源工具，具体的配置教程还是要参考AList和rclone的说明：

其中rclone挂载本地磁盘利用的是AList提供的webdav功能，比如百度网盘自身不提供webdav功能，所以利用AList挂在百度网盘接口，再利用AList自身的webdav接口从而产生百度网盘webdav的效果；

因为百度网盘的限制，大于20M的文件需要User Agent，否则网页端观看视频和下载文件会报错{"error_code":31362,"error_msg":"sign error","error_info":"","request_id":3389658821914890461}，同时这也是rclone挂在本地磁盘后报错的信息，所以与rclone无关，是因为AList挂载百度网盘的限制所导致的，这个时候需要在AList中设置webdav为本地代理，就可以正常使用rclone了；
更正：使用cmd命令行来rclone mount的话，添加--header "Referer:https://pan.baidu.com/"  --header "User-Agent:pan.baidu.com"参数后，不需要在AList中设置webdav为本地代理而是默认的重定向302也可以正常使用了，所以应该是AListHelper自身的bug，导致我在软件中设置该参数无法正确识别并运行，所以只能在AList中设置webdav为本地代理。
关于在AList中设置webdav为本地代理还是默认的重定向302，可以参考AList官方文档中的说明，重定向302性能损失较小，但每种网盘都需要设置对应的header；本地代理则使用搭建AList机器的本身带宽（其实影响不大）。

而AList本身使用百度网盘，则需要在网页端修改User Agent（麻烦），或者下载时对下载器单独设置User Agent（复制下载链接后用下载器下载就不会报错，同时使用网盘用户的自身速度），需要注意的是，User Agent在正常使用时需修改回来，否则正常资源会因为识别错误而无法下载。

<p align="center">
  <img src="https://github.com/Xmarmalade/alisthelper/assets/16839488/2067509c-756e-48cd-8f20-5ea961f46ef7" width="100" height="100">
</p>

English | [简体中文](./README_zh-Hans.md) |  [CODE_OF_CONDUCT](./CODE_OF_CONDUCT.md)

![](https://img.shields.io/badge/language-dart-blue.svg?style=for-the-badge&color=00ACC1)
![Downloads](https://img.shields.io/badge/flutter-00B0FF?style=for-the-badge&logo=flutter)
[![](https://img.shields.io/github/downloads/Xmarmalade/alisthelper/total?style=for-the-badge&color=FF2196)](https://github.com/Xmarmalade/alisthelper/releases)
[![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/Xmarmalade/alisthelper?include_prereleases&style=for-the-badge)](https://github.com/Xmarmalade/alisthelper/releases/latest)
[![](https://img.shields.io/github/license/Xmarmalade/alisthelper?style=for-the-badge)](./LICENSE)
![](https://img.shields.io/github/stars/Xmarmalade/alisthelper?style=for-the-badge)
![](https://img.shields.io/github/issues/Xmarmalade/alisthelper?style=for-the-badge&color=9C27B0)

Alist Helper is an application developed using Flutter, designed to simplify the use of the desktop version of alist. It can manage alist, allowing you to easily start and stop the alist program.

*Maintainer needed for the macOS part of the code. No new macOS-related changes or updates will be accepted until volunteers.*

### Screenshots
| ![image](https://github.com/Xmarmalade/alisthelper/assets/16839488/5b77df3a-8b07-40e4-adc5-9f0907f6a3f9) | ![image](https://github.com/Xmarmalade/alisthelper/assets/16839488/5a85db81-de92-4362-8c01-73e89482dcb7) |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| ![image](https://github.com/Xmarmalade/alisthelper/assets/16839488/0f28c3a0-aac5-40ac-87e1-e53ae597a738) | ![image](https://github.com/Xmarmalade/alisthelper/assets/16839488/e1b23c3c-cc62-4df8-8406-da41f798416e) |

Alist Helper includes several useful features:

- Automatic launching of alist
- Minimizing to the system tray
- Automatic startup on boot, with the option for silent startup
- Quick access to alist version and administrator information
- Adjustable alist startup parameters. You can customize the startup parameters to meet your specific needs and preferences.

Free. No tracking. No ads.

Currently, this app is available on Windows and macOS. Adaptation plans for more platforms are in progress.

Please note that this program does not include the binary files for alist. You will need to download them manually.

|                     | alist                        | alisthelper | alist desktop   |
| ------------------- | ---------------------------- | ----------- | --------------- |
| Price               | 🆓 Free                       | 🆓 Free      | 💰8$/50￥         |
| Startup at boot     | 🛠️ Needs manual configuration | ✅ Supported | ✅ Supported     |
| Silent startup      | ❌ Not supported              | ✅ Supported | ✅ Supported     |
| Accompanied startup | ❌ Not supported              | ✅ Supported | ✅ Supported     |
| GUI                 | ❌ Not supported              | ✅ Supported | ✅ Supported     |
| System tray         | ❌ Not supported              | ✅ Supported | ✅ Supported     |
| Startup parameters  | 🛠️ Needs manual configuration | ✅ Supported | ❌ Not supported |
| Http proxy          | 🛠️ Needs manual configuration | ✅ Supported | ❌ Not supported |

### Getting Started
[Wiki (Simplified Chinese language)](https://github.com/Xmarmalade/alisthelper/wiki)

## Contributing to AlistHelper

AlistHelper is an open-source project, and we welcome contributions from anyone who is interested in helping improve the app. Whether you're a developer, a translator, or a documentation writer, there are many ways to get involved.

### Getting Started

If you're interested in contributing code to AlistHelper, you'll need to follow these steps:

### Run

Fork the repository and install [Flutter](https://flutter.dev).

After you have installed [Flutter](https://flutter.dev), then you can start this app by typing the following commands:

```shell
flutter pub get
dart run build_runner build
flutter run
```

### Translation

You can help translating this app to other languages!

1. Fork this repository
2. Choose one
   - Add missing translations in existing languages: Only update `_missing_translations_<locale>.json` in [lib/i18n](https://github.com/Xmarmalade/alisthelper/tree/master/lib/i18n)
   - Fix existing translations: Update `strings_<locale>.i18n.json` in [lib/i18n](https://github.com/Xmarmalade/alisthelper/tree/master/lib/i18n)
   - Add new languages: Create a new file, see also: [locale codes](https://saimana.com/list-of-country-locale-code/).
3. Optional: Re-run this app
   1. Make sure you have [run](#run) this app once.
   2. Update translations via `dart run build_runner build`
   3. Run app via `flutter run`
4. Open a pull request

#### _Take note:_ Fields decorated with `@` are not meant to be translated, they are not used in the app in any way, being merely informative text about the file or to give context to the translator.

### Contributing Guidelines

Before you submit a pull request to AlistHelper, please ensure that you have followed these guidelines:

- Code should be well-documented and formatted according to the [Dart Style Guide](https://dart.dev/guides/language/effective-dart/style).
- All changes should be covered by tests.
- Commits should be well-written and descriptive, with a clear summary of the changes made and any relevant context.
- Pull requests should target the `master` branch and include a clear summary of the changes made.

### Bug Reports and Feature Requests

If you encounter a bug in AlistHelper or have a feature request, please submit an issue to the [issue tracker](https://github.com/Xmarmalade/alisthelper/issues). Please be sure to provide a clear description of the problem or feature request, along with any relevant context or steps to reproduce the issue.
