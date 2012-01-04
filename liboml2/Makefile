include $(TOPDIR)/rules.mk

PKG_NAME:=liboml2
PKG_VERSION:=2.6.1
PKG_RELEASE:=0
PKG_SOURCE_ID:=583


PKG_BUILD_DIR:=$(BUILD_DIR)/oml2-$(PKG_VERSION)
PKG_SOURCE:=oml2-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://omf.mytestbed.net/attachments/download/${PKG_SOURCE_ID}/
PKG_MD5SUM=d11c1cfb55488cf7f1ec1c6ede68bca4
PKG_CAT:=zcat
PKG_FIXUP:=autoreconf

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/liboml2
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OML2 Library
  URL:=http://mytestbed.net
  DEPENDS:=+libxml2 +libsqlite3 +libpopt
endef

define Package/liboml2/description
OMF is a framework for controlling, instrumenting, and managing testbeds.

Researchers use OMF to describe, execute, and analyse their experiments.

Testbed owners use OMF to make resources in the testbed discoverable, 
control access to them, optimise their utilisation through virtualisation, 
and federate with other testbeds.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/ocomm \
		$(1)/usr/include/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/oml2 \
		$(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/liboml2.{la,a,so*} \
		$(1)/usr/lib/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libocomm.{la,a,so*} \
		$(1)/usr/lib/
	
	$(INSTALL_DIR) $(2)/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2_scaffold \
		$(2)/bin/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/oml2-scaffold \
		$(2)/bin/
endef

define Package/liboml2/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/liboml2.so* \
		$(1)/usr/lib/
	
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libocomm.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,liboml2))
