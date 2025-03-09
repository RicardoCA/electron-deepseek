# Mantenedor: ricardocorreaandrade@proton.me
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
  # Clona o repositório diretamente para /opt/
  git clone "https://github.com/RicardoCA/electron-deepseek.git" "$srcdir/$pkgname"
  
  # Instala as dependências do npm
  cd "$srcdir/$pkgname"
  npm install
}

build() {
  # Se necessário, execute um build (caso tenha um processo específico)
  cd "$srcdir/$pkgname"
  npm run build  # Substitua pelo comando de build correto do seu projeto
}

package() {
  # Copia os arquivos para /opt/electron-deepseek
  mkdir -p "$pkgdir/opt/$pkgname"
  cp -r "$srcdir/$pkgname/"* "$pkgdir/opt/$pkgname/"
  
  # Cria um script de inicialização para o aplicativo
  mkdir -p "$pkgdir/usr/bin"
  echo '#!/bin/sh' > "$pkgdir/usr/bin/$pkgname"
  echo "npm start --converge /opt/$pkgname" >> "$pkgdir/usr/bin/$pkgname"
  chmod +x "$pkgdir/usr/bin/$pkgname"
  
  # Cria o arquivo .desktop
  mkdir -p "$pkgdir/usr/share/applications"
  echo "[Desktop Entry]
Name=Electron DeepSeek
Comment=Descrição do seu aplicativo electron-deepseek
Exec=npm start --converge /opt/$pkgname
Terminal=false
Type=Application
Categories=Utility;
Icon=/opt/$pkgname/icon.png" > "$pkgdir/usr/share/applications/$pkgname.desktop"
}
