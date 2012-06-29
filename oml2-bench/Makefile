include $(TOPDIR)/rules.mk

PKG_NAME:=oml2-bench
PKG_VERSION:=1.0.0
PKG_RELEASE:=1


PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=master
PKG_SOURCE_URL:=https://github.com/nathansamson/OML2-Bench.git
PKG_SOURCE_SUBDIR:=oml2-bench-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/oml2-bench
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OML And OMF Benchmarker
  URL:=http://nathansamson.be
  DEPENDS:=+liboml2
endef

define Package/oml2-bench/description
OML is a measurement library that allows application writers to define 
customizable measurement points inside applications. Experimenters running 
the applications can then direct the measurement streams from these measurement 
points to storage in a remote measurement database. OML was originally conceived
to provide measurement facilities within the OMF Testbed Management Framework, 
but can also be run independent of OMF.

endef

define Build/Compile
	
	gcc -I$(STAGING_DIR)/usr/include -o $(PKG_BUILD_DIR)/oml2-bench $(PKG_BUILD_DIR)/oml2-bench.c -loml2
endef

define Package/oml2-bench/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_BUILD_DIR)/oml2-bench \
		$(1)/usr/bin/
endef

$(eval $(call BuildPackage,oml2-bench))
