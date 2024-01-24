# Maintainer: Kimiblock Moe
_name="Amulet-Map-Editor"
pkgname="amulet-map-editor"

pkgdesc="The new age Minecraft world editor and converter that supports every version since Java 1.12 and Bedrock 1.7"
url="https://www.amuletmc.com/"
license=(custom)

arch=(any)
pkgver=0.10.27
pkgrel=3
makedepends=(python-build python-installer python-wheel python-cython-lint python-versioneer)

depends=(python python-numpy python-wxpython python-opengl python-amulet-nbt python-pymctranslate python-minecraft-model-reader python-amulet-core)

source=(
	amulet.desktop
	icon.png
	"https://github.com/Amulet-Team/${_name}/archive/refs/tags/${pkgver}.tar.gz}"
)

sha256sums=(
	"SKIP"
	"SKIP"
	"SKIP"
)

function prepare() {
	sed -i 's/versioneer-518/versioneer/g' "${srcdir}/Amulet-Map-Editor/pyproject.toml"
}

function build() {
	cd "${srcdir}/${_name}"
	python -m build --wheel --no-isolation
}

function package() {
	install -Dm755 "${srcdir}/icon.png" "${pkgdir}/usr/share/icons/hicolor/256x256/apps/amulet.png"
	install -Dm644 "${srcdir}/amulet.desktop" "${pkgdir}/usr/share/applications/amulet.desktop"
	cd "${srcdir}/${_name}"
	python -m installer --destdir="${pkgdir}" dist/*.whl
}
