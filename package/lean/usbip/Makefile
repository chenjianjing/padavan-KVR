include $(TOPDIR)/rules.mk

PKG_NAME:=usbip
PKG_VERSION:=3.18.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@KERNEL/linux/utils/usb/usbip
PKG_MD5SUM:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/usbip
    SECTION:=net
    CATEGORY:=Network
    TITLE:=USB/IP tools
    DEPENDS:=+libudev +kmod-usbip-core +kmod-usbip-vudc +kmod-usbip-host
    URL:=http://usbip.sourceforge.net/
endef

define Package/usbip/description
    USB/IP tools for sharing USB devices over IP network
endef

define Package/usbip/install
    $(INSTALL_DIR) $(1)/usr/sbin
    $(CP) $(PKG_INSTALL_DIR)/usr/sbin/usbip $(1)/usr/sbin/
    $(CP) $(PKG_INSTALL_DIR)/usr/sbin/usbipd $(1)/usr/sbin/
    
    $(INSTALL_DIR) $(1)/etc/init.d
    $(CP) ./files/usbip-server.init $(1)/etc/init.d/usbip-server
    chmod 755 $(1)/etc/init.d/usbip-server
endef

$(eval $(call BuildPackage,usbip))
