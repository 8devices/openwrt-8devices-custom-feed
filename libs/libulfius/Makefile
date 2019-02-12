
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=67f5fa7

PKG_NAME:=libulfius
PKG_VERSION:=2.5.3-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/babelouest/ulfius.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel
CMAKE_OPTIONS+=DWITH_JOURNALD=off
CMAKE_OPTIONS+=-DBUILD_SHARED_LIBS=ON

TARGET_CFLAGS += -D_GNU_SOURCE

define Package/libulfius
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Ulfius
  DEPENDS:=+liborcania +libyder +libgnutls
  URL:=https://github.com/babelouest/ulfius
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libulfius* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef


define Package/libulfius/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libulfius* $(1)/usr/lib
endef


$(eval $(call BuildPackage,libulfius,+liborcania,+libyder,+libgnutls))
