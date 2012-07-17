include $(TOPDIR)/rules.mk

PKG_NAME:=oml-iperf
PKG_VERSION:=2.0.5
PKG_RELEASE:=1
PKG_SOURCE_ID:=725

PKG_BUILD_DIR:=$(BUILD_DIR)/oml2-iperf-$(PKG_VERSION)+oml1
PKG_SOURCE:="iperf-$(PKG_VERSION) oml2.8.0.tar.gz"
PKG_SOURCE_URL:=http://oml2.mytestbed.net/attachments/download/${PKG_SOURCE_ID}/
PKG_MD5SUM=4166bcc03c1dfd557869bd4899ea1d16
PKG_CAT:=zcat
PKG_FIXUP:=autoreconf

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/oml-iperf
  SECTION:=base
  CATEGORY:=OMF
  DEFAULT:=n
  TITLE:=OML2 IPerf
  URL:=http://mytestbed.net
  DEPENDS:=+liboml2 +USE_UCLIBC:uclibcxx +!USE_UCLIBC:libstdcpp
endef

ifdef CONFIG_USE_UCLIBC
  TARGET_CXX=g++-uc
endif

define Package/oml-iperf/description
This project is meant to implement OML support for Iperf 2.0.5.
endef

define Package/oml-iperf/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/iperf \
		$(1)/usr/bin/oml2-iperf
endef

$(eval $(call BuildPackage,oml-iperf))
