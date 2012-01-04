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

include $(INCLUDE_DIR)/package.mk

define Package/oml2-apps
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OML2 Applications
  URL:=http://mytestbed.net
  DEPENDS+= liboml2
endef

define Package/oml2-apps/description
OMF is a framework for controlling, instrumenting, and managing testbeds.

Researchers use OMF to describe, execute, and analyse their experiments.

Testbed owners use OMF to make resources in the testbed discoverable, 
control access to them, optimise their utilisation through virtualisation, 
and federate with other testbeds.

endef

$(eval $(call BuildPackage,oml2-apps))
