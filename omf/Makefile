include $(TOPDIR)/rules.mk

PKG_NAME:=omf
PKG_VERSION:=5.4.2
PKG_RELEASE:=1
MAJOR_MINOR_VERSION=5.4

# Tries to download from openwrt => obviously this does not work, 
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=confine-5.4
PKG_SOURCE_URL:=https://github.com/nathansamson/OMF.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

RUBY_LIB_VER:=1.9

include $(INCLUDE_DIR)/package.mk

define Package/omf/Default
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OMF
  URL:=http://mytestbed.net
  DEPENDS+= +ruby +ruby-gems
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
  DEPENDS+= +ruby-log4r +xmpp4r +ruby-core +ruby-yaml +ruby-enc +ruby-rexml +ruby-openssl
endef

define Package/omf/description
$(call Package/omf/Default/description)
endef

define Package/omf-resctl
$(call Package/omf/Default)
  TITLE+=Resource Controller
  DEPENDS:=omf +wget +wireless-tools +pciutils +net-tools-hostname +@BUSYBOX_CONFIG_MODPROBE
  # If installing OMF, defaults installing omf-resctl.
  DEFAULT=:y
endef

define Package/omf-resctl/description
 Resource Controller.
endef

define Package/omf-resctl/conffiles
/etc/omf-resctl-$(MAJOR_MINOR_VERSION)/omf-resctl.yaml
endef

define Build/Compile
	# Nothing to build, its ruby!!
endef

define Package/helper/install
	# create directories
	$(INSTALL_DIR) $(1)/usr/share/$(2)-$(MAJOR_MINOR_VERSION)
	$(INSTALL_DIR) $(1)/etc/$(2)-$(MAJOR_MINOR_VERSION)
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d/
	
	$(CP) $(BUILD_DIR)/${PKG_SOURCE_SUBDIR}/$(2)/ruby/* \
		$(1)/usr/share/$(2)-$(MAJOR_MINOR_VERSION)/
	$(CP) $(BUILD_DIR)/${PKG_SOURCE_SUBDIR}/$(2)/sbin/$(2) \
		$(1)/usr/bin
	$(CP) $(BUILD_DIR)/${PKG_SOURCE_SUBDIR}/$(2)/etc/$(2)/* \
		$(1)/etc/$(2)-$(MAJOR_MINOR_VERSION)
	$(CP) ./files/$(2).init $(1)/etc/init.d/
	
	$(INSTALL_DATA) ./files/$(2).yaml $(1)/etc/$(2)-$(MAJOR_MINOR_VERSION)/
endef

define Package/omf/install
	$(INSTALL_DIR) $(1)/usr/share/omf-common-$(MAJOR_MINOR_VERSION)
	
	$(CP) $(BUILD_DIR)/${PKG_SOURCE_SUBDIR}/omf-common/ruby/* \
		$(1)/usr/share/omf-common-$(MAJOR_MINOR_VERSION)/
		
	$(INSTALL_DIR) $(1)/usr/lib/ruby/$(RUBY_LIB_VER)/wss4r/security/util
	$(CP) $(BUILD_DIR)/${PKG_SOURCE_SUBDIR}/wss4r/xmlcanonicalizer.rb \
		$(1)/usr/lib/ruby/$(RUBY_LIB_VER)/wss4r/security/util/
endef

define Package/omf-resctl/install
$(call Package/helper/install,$(1),omf-resctl)
endef

$(eval $(call BuildPackage,omf))	
$(eval $(call BuildPackage,omf-resctl))
