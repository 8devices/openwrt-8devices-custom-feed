
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=02be896

PKG_NAME:=punica
PKG_VERSION:=0.1.0-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/punica/punica.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_BUILD_DEPENDS:=argp-standalone

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel
CMAKE_OPTIONS+=-DPUNICA_VERSION=$(PKG_VERSION)

define Package/punica
  SECTION:=net
  CATEGORY:=Network
  TITLE:=punica
  DEPENDS:=+libmbedtls +libgcrypt +libcurl +jansson +libtasn1 +p11-kit +zlib +libwakaama +libuuid
  URL:=https://github.com/punica/punica.git
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

define Package/punica/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/punica $(1)/usr/bin/punica
endef

$(eval $(call BuildPackage,punica))
