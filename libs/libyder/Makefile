
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=c64f1e3

PKG_NAME:=libyder
PKG_VERSION:=1.4.4-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/babelouest/yder.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DWITH_JOURNALD=off
CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel

TARGET_CFLAGS += -D_GNU_SOURCE

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

define Package/libyder
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=yder
  DEPENDS:=+libstdcpp +libcurl +libmicrohttpd +jansson
  URL:=https://github.com/babelouest/yder
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libyder* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef


define Package/libyder/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libyder.so* $(1)/usr/lib/
endef


$(eval $(call BuildPackage,libyder))
