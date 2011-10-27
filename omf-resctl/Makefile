include $(TOPDIR)/rules.mk

PKG_NAME:=omf-resctl
PKG_VERSION:=5.3
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=omf-5.3.1-stable
PKG_SOURCE_URL:=git://git.mytestbed.net/omf.git
# Tries to download from openwrt => obviously this does not work, 
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/omf-resctl
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OMF Resource Controller
  URL:=http://mytestbed.net
  DEPENDS+= +ruby +omf-common
endef

define Package/omf-resctl/description
 Ethernet bridging configuration utility
 Manage ethernet bridging; a way to connect networks together to
 form a larger network.
endef

define Build/Compile
	# Nothing to build, its ruby!!
endef

define Package/omf-resctl/install
	# create directories
	$(INSTALL_DIR) $(1)/usr/share/omf-resctl-$(PKG_VERSION)
	$(INSTALL_DIR) $(1)/etc/omf-resctl-$(PKG_VERSION)
	$(CP) $(BUILD_DIR)/${PKG_NAME}/ruby/omf-resctl/* $(1)/usr/share/omf-resctl-$(PKG_VERSION)/

endef

$(eval $(call BuildPackage,omf-resctl))

