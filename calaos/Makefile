#
# Copyright (C) 2015 Calaos
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=calaos
PKG_VERSION:=2.99
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/calaos/calaos_base.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=51f82c4e1c739e256801efa9044761f57d9ad2d6
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MAINTAINER:=Nicolas Aguirre <nico@calaos.fr>
PKG_LICENSE:=GPL-3.0


PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/calaos
  SECTION:=Calaos
  CATEGORY:=Calaos
  TITLE:=Calaos
  DEPENDS:=+eina +eet +ecore +curl +libsigcxx +gettext +jansson +lua +libstdcpp
endef

define Package/calaos/Default
  URL:=https://calaos.fr
  SUBMENU:=Filesystem
endef


define Package/calaos/description
  Calaos Home Automation solution
endef

EXTRA_LDFLAGS += -Wl,-rpath-link=$(STAGING_DIR)/usr/lib -Wl,-Map,calaos_server.map -Wl,--gc-section
EXTRA_CFLAGS += -std=c++11 -ffunction-sections -fdata-sections

define Build/Configure
	(cd $(PKG_BUILD_DIR); NOCONFIGURE=YES ./autogen.sh );
	$(call Build/Configure/Default)
endef

define Build/Compile
	DESTDIR="$(PKG_INSTALL_DIR)" $(MAKE) -C $(PKG_BUILD_DIR) all install
endef

define Package/calaos/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
endef

$(eval $(call BuildPackage,calaos))
