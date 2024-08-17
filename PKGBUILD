pkgname=fido2-hid-bridge-git
pkgver=r29.6aa6c20
pkgrel=1
pkgdesc='FIDO2 NFC to USB HID bridge'
arch=('x86_64')
url='https://github.com/BryanJacobs/fido2-hid-bridge'
license=('MIT')
depends=('pcsclite')
makedepends=('git' 'python-poetry' 'swig')
source=("fido2-hid-bridge::git+${url}")
sha512sums=('SKIP')

pkgver() {
  set -euo pipefail
  cd "fido2-hid-bridge"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "fido2-hid-bridge"
  #python -m build --wheel --no-isolation
  poetry install
}

package() {
  cd "fido2-hid-bridge"
  mkdir -p "${pkgdir}/opt/fido2-hid-bridge/"
  cp -a ".venv" "${pkgdir}/opt/fido2-hid-bridge/.venv"
  install -Dm 644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  install -Dm 644 fido2-hid-bridge.service "${pkgdir}/usr/lib/systemd/system/fido2-hid-bridge.service"
}
