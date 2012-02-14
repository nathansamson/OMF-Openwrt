include $(TOPDIR)/rules.mk

PKG_NAME:=libsigar
PKG_VERSION:=1.6.999
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=master
PKG_SOURCE_URL:=git://github.com/hyperic/sigar.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libsigar
  SECTION:=libs
  CATEGORY:=Libraries
  DEFAULT:=n
  TITLE:=SIGAR - System Information Gatherer And Reporter
  URL:=http://support.hyperic.com/display/SIGAR/Home
endef

define Package/libgsigar/description
The Sigar API provides a portable interface for gathering system information such as:

    System memory, swap, cpu, load average, uptime, logins
    Per-process memory, cpu, credential info, state, arguments, environment, open files
    File system detection and metrics
    Network interface detection, configuration info and metrics
    TCP and UDP connection tables
    Network route table

This information is available in most operating systems, but each OS has their own way(s) providing it.
SIGAR provides developers with one API to access this information regardless of the underlying platform.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include
	
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/{*.a,*.so.*} \
		$(1)/usr/lib
endef

define Package/libsigar/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libsigar.so \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsigar))
