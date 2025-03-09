# Mantenedor: [Seu nome e email]
pkgname=electron-deepseek
pkgver=1.0.0  # Substitua pela versão do seu projeto
pkgrel=1
pkgdesc="Descrição do seu aplicativo electron-deepseek"
arch=('x86_64')
url="https://github.com/RicardoCA/electron-deepseek"  # Substitua pelo URL correto
license=('MIT')  # Substitua pela licença correta
depends=('electron' 'gtk3' 'nss' 'libxss')
makedepends=('npm' 'git' 'nodejs')
source=("git+https://github.com/RicardoCA/electron-deepseek.git")
sha256sums=('SKIP')

prepare() {
  cd "$pkgname"
  npm install
}

build() {
  cd "$pkgname"
  npm run build  # Substitua pelo comando de build correto do seu projeto
}

package() {
  cd "$pkgname"
  
  # Cria diretórios necessários
  mkdir -p "$pkgdir/usr/lib/$pkgname"
  mkdir -p "$pkgdir/usr/bin"
  mkdir -p "$pkgdir/usr/share/applications"
  
  # Copia arquivos do aplicativo
  cp -r /* "$pkgdir/usr/lib/$pkgname/"
  
  # Cria um script para iniciar o aplicativo
  echo '#!/bin/sh' > "$pkgdir/usr/bin/$pkgname"
  echo "electron /usr/lib/$pkgname" >> "$pkgdir/usr/bin/$pkgname"
  chmod +x "$pkgdir/usr/bin/$pkgname"
  
  # Cria um arquivo .desktop para o menu de aplicativos
  echo "[Desktop Entry]
Name=Electron DeepSeek
Comment=Descrição do seu aplicativo electron-deepseek
Exec=npm start $pkgname
Terminal=false
Type=Application
Categories=Utility;
Icon=/usr/lib/$pkgname/icon.png" > "$pkgdir/usr/share/applications/$pkgname.desktop"
}