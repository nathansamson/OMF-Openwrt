include $(TOPDIR)/rules.mk

PKG_NAME:=omf
PKG_VERSION:=5.3
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=omf-5.3.1-stable
PKG_SOURCE_URL:=git://git.mytestbed.net/omf.git
PKG_SOURCE_SUBDIR=omf
# Tries to download from openwrt => obviously this does not work, 
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/omf/Default
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OMF
  URL:=http://mytestbed.net
  DEPENDS+= +ruby
endef

define Package/omf/Default/description
OMF is a framework for controlling, instrumenting, and managing testbeds.

Researchers use OMF to describe, execute, and analyse their experiments.

Testbed owners use OMF to make resources in the testbed discoverable, 
control access to them, optimise their utilisation through virtualisation, 
and federate with other testbeds.

endef

define Package/omf
$(call Package/omf/Default)
  TITLE+=cOntrol and Management Framework
  DEPENDS+= +ruby-log4r +xmpp4r +ruby-core +ruby-yaml
endef

define Package/omf/description
$(call Package/omf/Default/description)
endef

define Package/omf-resctl
$(call Package/omf/Default)
  TITLE+=Resource Controller
  DEPENDS:=omf +wget +wireless-tools +pciutils
  # If installing OMF, defaults installing omf-resctl.
  DEFAULT=:y
endef

define Package/omf-resctl/description
 Resource Controller.
endef

define Build/Compile
	# Nothing to build, its ruby!!
endef

define Package/helper/install
	# create directories
	$(INSTALL_DIR) $(1)/usr/share/$(2)-$(PKG_VERSION)
	$(INSTALL_DIR) $(1)/etc/$(2)-$(PKG_VERSION)
	$(INSTALL_DIR) $(1)/usr/bin
	
	$(CP) $(BUILD_DIR)/omf/$(2)/ruby/* \
		$(1)/usr/share/$(2)-$(PKG_VERSION)/
	$(CP) $(BUILD_DIR)/omf/$(2)/sbin/$(2) \
		$(1)/usr/bin
	$(CP) $(BUILD_DIR)/omf/$(2)/etc/$(2)/* \
		$(1)/etc/$(2)-$(PKG_VERSION)
endef

define Package/omf/install
	$(INSTALL_DIR) $(1)/usr/share/omf-common-$(PKG_VERSION)
	
	$(CP) $(BUILD_DIR)/omf/omf-common/ruby/* \
		$(1)/usr/share/omf-common-$(PKG_VERSION)/
endef

define Package/omf-resctl/install
$(call Package/helper/install,$(1),omf-resctl)
endef

$(eval $(call BuildPackage,omf))
$(eval $(call BuildPackage,omf-resctl))
