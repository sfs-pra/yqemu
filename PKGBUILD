# Maintainer: sfslinux@gmail.com

pkgname=yqemu
pkgver=r5.9a0b8b9
pkgrel=1
pkgdesc="QEMU GUI written in yad"
arch=('any')
url="https://forum.puppyrus.org/index.php?topic=3840.msg189484#msg189484"
license=('GPL3')
depends=(
yad-light
gettext
bash
coreutils
grep
sed
gawk
edk2-ovmf
qemu-audio-alsa
qemu-base
qemu-common
qemu-hw-display-virtio-vga-gl
qemu-img
qemu-system-x86
qemu-system-x86-firmware
qemu-ui-gtk
qemu-ui-opengl
)
source=("git+https://github.com/sfs-pra/yqemu.git")
sha256sums=('SKIP')
install=$pkgname.install

pkgver() {
    cd "${srcdir}/${pkgname}"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir/$pkgname"

  # Install the script
  install -Dm755 $pkgname -t "$pkgdir/usr/bin/"
  install -Dm755 ${pkgname}-img -t "$pkgdir/usr/bin/"

  # Install the .desktop file
  install -Dm644 $pkgname.desktop -t "$pkgdir/usr/share/applications/"

  mkdir -p $pkgdir/usr/share/locale/ru/LC_MESSAGES
  msgfmt po/ru.po -o "$pkgdir/usr/share/locale/ru/LC_MESSAGES/$pkgname.mo"
}
