#
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 4855 2006-09-24 20:49:31Z nico $

include $(TOPDIR)/rules.mk

PKG_NAME:=mono
PKG_VERSION:=2.0.1
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://ftp.novell.com/pub/mono/sources/mono
PKG_SOURCE:=mono-$(PKG_VERSION).tar.bz2
PKG_CAT:=bzcat

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/mono
	SECTION:=lang
	CATEGORY:=Languages
	TITLE:=.NET Mono Support
	MAINTAINER:=ajlennon@dynamicdevices.co.uk
#	DEPENDS:=+libsocketcpp
	DEPENDS:=+glib2
endef

define Package/mono/description
	.NET Mono
endef

define Build/Configure	
	$(call Build/Configure/Default, \
		$(DISABLE_NLS) \
		CC_FOR_BUILD=mipsel-linux-uclibc-gcc \
		--with-tls=pthread \
	) 
endef

define Build/InstallDev
#	$(INSTALL_DIR) $(1)/usr/lib	
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/libopenobex*.{la,so*,a} $(1)/usr/lib/	

#	$(INSTALL_DIR) $(1)/usr/include/openob	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/openobex/*.h $(1)/usr/include/openobex	
#
#	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig	
#	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/openobex.pc $(1)/usr/lib/pkgconfig/	
endef

define Package/mono/install
	$(INSTALL_DIR) $(1)/etc/mono
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/mono/browscap.ini $(1)/etc/mono
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/mono/config $(1)/etc/mono
	$(INSTALL_DIR) $(1)/etc/mono/1.0
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/mono/1.0/*.{aspx,config} $(1)/etc/mono/1.0
	$(INSTALL_DIR) $(1)/etc/mono/2.0
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/mono/2.0/*.{aspx,config,map} $(1)/etc/mono/2.0
	$(INSTALL_DIR) $(1)/etc/mono/2.0/Browsers
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/etc/mono/2.0/Browsers/* $(1)/etc/mono/2.0/Browsers
	$(INSTALL_DIR) $(1)/usr	
	$(INSTALL_DIR) $(1)/usr/bin	
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
#	$(INSTALL_DIR) $(1)/usr/include	
#	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib	
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/*.{a,so*} $(1)/usr/lib/
#	$(INSTALL_DIR) $(1)/usr/man
#	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/man/* $(1)/usr/man/
#	$(INSTALL_DIR) $(1)/usr/share	
#	$(INSTALL_DIR) $(1)/usr/share/libgc-mono
#	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
endef

$(eval $(call BuildPackage,mono))
