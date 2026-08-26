#
# Copyright (C) 2017-2020
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qbittorrent-nox-static
PKG_VERSION:=5.2.3
PKG_RELEASE:=2

PKG_FULL_VERSION:=5.2.3_v2.0.14

STRIP:=true

ifeq ($(ARCH),i386)
	PKG_ARCH:=x86
	PKG_HASH:=b4519d313304780375e876fffbf668b4385496dd8e4a5fa7d1eebb33e6dc2f10
endif

ifeq ($(ARCH),x86_64)
	PKG_ARCH:=x86_64
	PKG_HASH:=c1839caf9b7dbddee09e9a4394bb5b17dc70ecd7c3a9b45e84331d5a1389a645
endif

ifeq ($(ARCH),aarch64)
	PKG_ARCH:=aarch64
	PKG_HASH:=de4239e0c8683e26b970c25e1fe27fb6336635300553f8f0bda2d60299f60ed1
endif

ifeq ($(ARCH),arm)
	PKG_ARCH:=armv7
	PKG_HASH:=d094161e14a046eeef774155de3831bd52a0ce6c315dfe0c939af0d3dfce246b
endif

include $(INCLUDE_DIR)/package.mk

define Package/qbittorrent-nox-static
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=@(arm||aarch64||i386||x86_64)
	SUBMENU:=BitTorrent
	TITLE:=bittorrent client programmed in C++ / Qt
	URL:=https://github.com/userdocs/qbittorrent-nox-static
	PROVIDES:=qBittorrent
endef

define Package/qbittorrent-nox-static/description
  The qbittorrent-nox-static project is a bash build script that compiles
  a static qbittorrent-nox binary using the latest available dependencies
  from their source. These statically linked binaries can run on any
  matching CPU architecture and are not OS specific.

  See: https://github.com/userdocs/qbittorrent-nox-static
endef

define Download/qbittorrent-nox-static
	URL:=https://github.com/userdocs/qbittorrent-nox-static/releases/download/release-$(PKG_FULL_VERSION)
	URL_FILE:=$(PKG_ARCH)-qbittorrent-nox
	FILE:=qbittorrent-nox-$(PKG_ARCH)-$(PKG_FULL_VERSION)
	HASH:=$(PKG_HASH)
endef

define Package/qbittorrent-nox-static/conffiles
/etc/config/qbittorrent
endef

define Build/Compile
endef

define Package/qbittorrent-nox-static/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(DL_DIR)/qbittorrent-nox-$(PKG_ARCH)-$(PKG_FULL_VERSION) $(1)/usr/bin/qbittorrent-nox

	$(INSTALL_DIR) $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_BIN) ./files/qbittorrent.init $(1)/etc/init.d/qbittorrent
	$(INSTALL_CONF) ./files/qbittorrent.conf $(1)/etc/config/qbittorrent
endef

$(eval $(call Download,qbittorrent-nox-static))
$(eval $(call BuildPackage,qbittorrent-nox-static))

