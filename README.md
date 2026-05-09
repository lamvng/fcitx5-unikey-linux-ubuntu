# Fcitx5 Unikey Linux Ubuntu

(Xem hướng dẫn tiếng Anh ở bên dưới)

## Hướng dẫn tiếng Việt

Hướng dẫn cài đặt Fcitx5 Unikey (bộ gõ tiếng Việt cho Linux) trên Ubuntu. Đã thử thành công trên Ubuntu 26.04 LTS (GNOME, Wayland).

### Cài packages

```bash
sudo apt install fcitx5 fcitx5-config-qt fcitx5-unikey
```

Sau khi cài, một icon hình bàn phím sẽ xuất hiện ở góc trên bên phải màn hình, gần các icons wifi, bluetooth và pin. Ấn vào hình bàn phím đó, chọn "Input Method Settings." để mở UI. Bỏ check "Only Show Current Language," sau đó nhập "Unikey" vào ô "Search Input Method". Chọn Unikey và nhấn đúp chuột.

### Cài autostart

```bash
mkdir -p ~/.config/autostart && cp /usr/share/applications/org.fcitx.Fcitx5.desktop ~/.config/autostart
```

Việc cài đặt đã xong. Ấn tổ hợp phím tắt Ctrl+Space để chuyển qua lại giữa tiếng Việt và tiếng Anh.

<details>

<summary>Không bắt buộc - Sửa lỗi input popup</summary>


Sau khi cài đặt, đôi khi sẽ thấy thông báo lỗi sau trên Ubuntu Notification:

> Wayland diagnose: It is recommended to install Input Method Panel GNOME Shell Extensions to provide the input method popup. https://extensions.gnome.org/extension/261/kimpanel/. Otherwise you may not be able to see input method popup when typing GNOME shell's activities search box. For more details see https://fcitx-im.org/wiki/Using_Fcitx_5_on_Wayland#GNOME.

Lỗi này chỉ ảnh hưởng đến một số trường hợp rất cụ thể nếu dùng Fcitx5 để gõ tiếng Trung, Nhật, Hàn và chỉ xảy ra trên GNOME Activities search box (người viết không tìm cách replicate lỗi này). Trong đa số trường hợp, bạn có thể bỏ qua lỗi này. Nhấn "Do not show again." để bỏ qua thông báo.

Nếu cần fix, phải cài thêm GNOME extension. Làm như sau:

### Xem version của GNOME Shell

```bash
gnome-shell --version
```

### Download extension

Download extension trên https://extensions.gnome.org/extension/261/kimpanel/, chọn bản gần với version của Shell nhất.

### Cài extension

```bash
mkdir -p ~/.local/share/gnome-shell/extensions/kimpanel@kde.org
unzip ~/Downloads/kimpanelkde.org.${version}.shell-extension.zip -d ~/.local/share/gnome-shell/extensions/kimpanel@kde.org # Replace ${version} with the actual downloaded version
```

Log out và log in lại. Xem các GNOME shell extensions đã cài, kiểm tra xem có thấy `kimpanel@kde.org` hay không:

```bash
gnome-extensions list
```

#### Bật extension

```bash
gnome-extensions enable kimpanel@kde.org
```

</details>

## English text

Fcitx5 Unikey (Vietnamese keyboard for Linux) installation guide for Ubuntu. Tested on vanilla Ubuntu 26.04 LTS (GNOME, Wayland).

### Install required packages

```bash
sudo apt install fcitx5 fcitx5-config-qt fcitx5-unikey
```

After installation, a new icon should appear in the top-right corner of the screen, alongside the existing WiFi, Bluetooth, and battery icons. Click it and select "Input Method Settings." This opens the Fcitx Configuration UI. Uncheck "Only Show Current Language," then type "Unikey" in the "Search Input Method" field. Double-click on Unikey to add it to the list of active input methods.

### Configure application autostart

```bash
mkdir -p ~/.config/autostart && cp /usr/share/applications/org.fcitx.Fcitx5.desktop ~/.config/autostart
```

Installation is completed. Press Ctrl+Space to switch between languages.

<details>

<summary> Optional - Fix input popup issue </summary>

After installation, you may see the following notification:

> Wayland diagnose: It is recommended to install Input Method Panel GNOME Shell Extensions to provide the input method popup. https://extensions.gnome.org/extension/261/kimpanel/. Otherwise you may not be able to see input method popup when typing GNOME shell's activities search box. For more details see https://fcitx-im.org/wiki/Using_Fcitx_5_on_Wayland#GNOME.

This issue only affects very specific cases, mainly when using Fcitx5 for Chinese, Japanese, or Korean input in the GNOME Activities search box (the author did not try to replicate it). If this does not apply to you, you can safely ignore the message by clicking "Do not show again." to silence the nofitication.

On the contray, if you want to install the extension as recommended, follow these steps:

### Check GNOME Shell version

```bash
gnome-shell --version
```

### Download extension

Go to https://extensions.gnome.org/extension/261/kimpanel/, download the version closest to your GNOME Shell version.

### Install the extension

```bash
mkdir -p ~/.local/share/gnome-shell/extensions/kimpanel@kde.org
unzip ~/Downloads/kimpanelkde.org.${version}.shell-extension.zip -d ~/.local/share/gnome-shell/extensions/kimpanel@kde.org # Replace ${version} with the actual downloaded version
```

Log out and log back in. Verify the list of extensions:

```bash
gnome-extensions list
```

You should see `kimpanel@kde.org` in the list.

### Activate the extension:

```bash
gnome-extensions enable kimpanel@kde.org
```

</details>
