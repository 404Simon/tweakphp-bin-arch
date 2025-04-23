# Maintainer: Simon i22038@hb.dhbw-stuttgart.de
pkgname=tweakphp-bin
pkgver=0.7.2
pkgrel=1
pkgdesc="A modern PHP playground UI for local development"
arch=('x86_64' 'aarch64')
url="https://github.com/tweakphp/tweakphp"
license=('MIT')
depends=()
optdepends=(
    'fuse2: To run the AppImage'
    'fuse3: To run the AppImage'
)
options=(!strip)
source_x86_64=(
  "TweakPHP-${pkgver}.AppImage::https://github.com/tweakphp/tweakphp/releases/download/v${pkgver}/TweakPHP-${pkgver}.AppImage"
  "icon.png::https://raw.githubusercontent.com/tweakphp/tweakphp/main/build/icon.png"
  "LICENSE::https://raw.githubusercontent.com/tweakphp/tweakphp/v${pkgver}/LICENSE.md"
)
source_aarch64=(
  "TweakPHP-${pkgver}-arm64.AppImage::https://github.com/tweakphp/tweakphp/releases/download/v${pkgver}/TweakPHP-${pkgver}-arm64.AppImage"
  "icon.png::https://raw.githubusercontent.com/tweakphp/tweakphp/main/build/icon.png"
  "LICENSE::https://raw.githubusercontent.com/tweakphp/tweakphp/v${pkgver}/LICENSE.md"
)

sha256sums_x86_64=('bc5a56797a5a6e8b493bfdedd2585023bcbe1d13d8fb1bc625148bcc89118bf9'
                   '41ba6ba7838254a583c908b8ff62207e9495908797c599c4d6eb68488c180da8'
                   '8ad35d0f253a5750d3d38913525054d67e7b95f9b4f14cedac19b902fdafe84c')
sha256sums_aarch64=('5ca3e5512e53b8d0befa8d8c1257953e9dbaf36a8fc3e3f2c36c2dea9d56261c'
                   '41ba6ba7838254a583c908b8ff62207e9495908797c599c4d6eb68488c180da8'
                   '8ad35d0f253a5750d3d38913525054d67e7b95f9b4f14cedac19b902fdafe84c')

package() {
  local _appimage_src
  if [[ "$CARCH" == "x86_64" ]]; then
    _appimage_src="TweakPHP-${pkgver}.AppImage"
  elif [[ "$CARCH" == "aarch64" ]]; then
    _appimage_src="TweakPHP-${pkgver}-arm64.AppImage"
  else
    error "Unsupported architecture: $CARCH"
    return 1
  fi

  install -Dm755 "${_appimage_src}" "$pkgdir/opt/tweakphp/TweakPHP.AppImage"

  install -dm755 "$pkgdir/usr/bin"
  ln -s /opt/tweakphp/TweakPHP.AppImage "$pkgdir/usr/bin/tweakphp"

  install -Dm644 /dev/stdin "$pkgdir/usr/share/applications/tweakphp.desktop" <<EOF
[Desktop Entry]
Name=TweakPHP
Comment=${pkgdesc}
Exec=tweakphp
Icon=tweakphp
Type=Application
Categories=Development;
EOF

  install -Dm644 icon.png "$pkgdir/usr/share/icons/hicolor/256x256/apps/tweakphp.png"

  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
