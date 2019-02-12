
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=1944e90

PKG_NAME:=libjwt
PKG_VERSION:=1.2.9-2019-01-16-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/benmcollins/libjwt.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel
CMAKE_OPTIONS+=-DBUILD_SHARED_LIBS=ON

PKG_INSTALL:=1

TARGET_CFLAGS += -D_GNU_SOURCE
CONFIGURE_ARGS +=--without-openssl

define Package/libjwt
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=jwt
  DEPENDS:=+jansson +libgnutls +libopenssl
  URL:=https://github.com/benmcollins/libjwt.git
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjwt* $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/libjwt/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libjwt.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libjwt,+jansson,+libgnutls,+libopenssl))
