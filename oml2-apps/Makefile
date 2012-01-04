include $(TOPDIR)/rules.mk

PKG_NAME:=oml2-apps
PKG_VERSION:=2.5.0
PKG_RELEASE:=0
PKG_SOURCE_ID:=582


PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://oml.mytestbed.net/attachments/download/${PKG_SOURCE_ID}/
PKG_MD5SUM=d17ae839e21f50e5d654b8378e162e7b
PKG_CAT:=zcat
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/oml2-apps
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OML2 Applications
  URL:=http://mytestbed.net
  DEPENDS:=+libxml2 +libsqlite3 +libpopt +liboml2 +gpsd
endef

define Package/oml2-apps/description
OMF is a framework for controlling, instrumenting, and managing testbeds.

Researchers use OMF to describe, execute, and analyse their experiments.

Testbed owners use OMF to make resources in the testbed discoverable, 
control access to them, optimise their utilisation through virtualisation, 
and federate with other testbeds.
endef

define Package/oml2-apps/install
	$(INSTALL_DIR) $(1)/usr/lib/otg2
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/otg2/libotg2.so* \
		$(1)/usr/lib/otg2/
	
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-gpslogger \
		$(1)/usr/lib/
		
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-otg2 \
		$(1)/usr/lib/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-otr2 \
		$(1)/usr/lib/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-wlanconfig \
		$(1)/usr/lib/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/ripwave-monitor \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,oml2-apps))
