#
# Copyright (C) 2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=arp-scan
PKG_VERSION:=1.9.7
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/royhills/arp-scan/tar.gz/$(PKG_VERSION)?
PKG_HASH:=e03c36e4933c655bd0e4a841272554a347cd0136faf42c4a6564059e0761c039

PKG_MAINTAINER:=Sergey Urushkin <urusha.v1.0@gmail.com>
PKG_LICENSE:=GPL-3.0

PKG_FIXUP:=autoreconf

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/arp-scan
  SECTION:=net
  CATEGORY:=Network
  TITLE:=ARP scanner
  DEPENDS:=+libpcap
  URL:=https://github.com/royhills/arp-scan
  PKG_MAINTAINER:=Sergey Urushkin <urusha.v1.0@gmail.com>
endef

define Package/arp-scan/description
    ARP scanner
endef

define Package/arp-scan/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/usr/share/arp-scan
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/arp-scan $(1)/usr/bin/
	$(PKG_BUILD_DIR)/get-iab -v -u "http://standards-oui.ieee.org/iab/iab.txt" -f $(PKG_BUILD_DIR)/ieee-iab.txt
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ieee-iab.txt $(1)/usr/share/arp-scan/
	$(PKG_BUILD_DIR)/get-oui -v -u "http://standards-oui.ieee.org/oui/oui.txt" -f $(PKG_BUILD_DIR)/ieee-oui.txt
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ieee-oui.txt $(1)/usr/share/arp-scan/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/mac-vendor.txt $(1)/usr/share/arp-scan/
endef

$(eval $(call BuildPackage,arp-scan))
