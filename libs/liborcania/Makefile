
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=614754c

PKG_NAME:=liborcania
PKG_VERSION:=1.2.9-2019-01-16-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/babelouest/orcania.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel
CMAKE_OPTIONS+=-DBUILD_SHARED_LIBS=ON

TARGET_CFLAGS += -D_GNU_SOURCE

PKG_INSTALL:=1

define Package/liborcania
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=orcania
  DEPENDS:=+jansson
  URL:=https://github.com/babelouest/orcania
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/liborcania* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/liborcania/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/liborcania.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,liborcania,+jansson))
