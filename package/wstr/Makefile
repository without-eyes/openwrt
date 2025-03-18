include $(TOPDIR)/rules.mk

PKG_NAME:=wstr
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_SOURCE_DIR:=$(PKG_BUILD_DIR)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/wstr
  SECTION:=utils
  CATEGORY:=Network
  TITLE:=Without eyeS's Traceroute
endef

define Package/wstr/description
  Custom implementation of traceroute.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
	$(CP) ./include/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(CFLAGS) \
		$(PKG_BUILD_DIR)/*.c -o $(PKG_BUILD_DIR)/wstr \
		$(TARGET_LDFLAGS)
endef

define Package/wstr/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/wstr $(1)/usr/bin/
endef

define Build/Clean
	$(RM) -r $(PKG_BUILD_DIR)
endef

$(eval $(call BuildPackage,wstr))
