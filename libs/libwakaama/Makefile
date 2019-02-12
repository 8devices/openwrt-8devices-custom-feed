
include $(TOPDIR)/rules.mk

PKG_SOURCE_VERSION:=d8ee899

PKG_NAME:=libwakaama
PKG_VERSION:=2.5.3-$(PKG_SOURCE_VERSION)
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/punica/wakaama.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_SOURCE_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS+=-DCMAKE_BUILD_TYPE=MinSizeRel
CMAKE_OPTIONS+=-DBUILD_SHARED_LIBS=ON

TARGET_CFLAGS += -D_GNU_SOURCE

define Package/libwakaama
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=wakaama
  DEPENDS:=+libulfius +libjwt 
  URL:=https://github.com/babelouest/wakaama
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwakaama* $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/core/liblwm2m.h $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/examples/shared/*.h $(1)/usr/include
endef


define Package/libwakaama/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwakaama* $(1)/usr/lib
endef


$(eval $(call BuildPackage,libwakaama,+libulfius,+libjwt))
