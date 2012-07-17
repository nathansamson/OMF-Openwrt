include $(TOPDIR)/rules.mk

PKG_NAME:=oml2-apps
PKG_VERSION:=2.8.0
PKG_RELEASE:=0
PKG_SOURCE_ID:=724


PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://oml2.mytestbed.net/attachments/download/${PKG_SOURCE_ID}/
PKG_MD5SUM=513aea666234f520952449288904cce2
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
  DEPENDS:=+libxml2 +libsqlite3 +libpopt +liboml2 +gpsd +libsigar +libpcap
endef

define Package/oml2-apps/description
OML is a measurement library that allows application writers to define 
customizable measurement points inside applications. Experimenters running 
the applications can then direct the measurement streams from these measurement 
points to storage in a remote measurement database. OML was originally conceived
to provide measurement facilities within the OMF Testbed Management Framework, 
but can also be run independent of OMF.

This is a set of applications that collect measurements.
It consists of the following applications.

    oml2-otg2 (as otg2)
    oml2-otr2 (as otr2)
    oml2-gpslogger -- The GPS app;
    oml2-wlanconfig -- Records wifi info from wlanconfig;
    ripwave-monitor

endef

define Package/oml2-apps/install
	$(INSTALL_DIR) $(1)/usr/lib/otg2
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/otg2/libotg2.so* \
		$(1)/usr/lib/otg2/
	
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-gpslogger \
		$(1)/usr/bin/
		
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-otg2 \
		$(1)/usr/bin/otg2
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-otr2 \
		$(1)/usr/bin/otr2
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-wlanconfig \
		$(1)/usr/bin/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/ripwave-monitor \
		$(1)/usr//
endef

$(eval $(call BuildPackage,oml2-apps))
