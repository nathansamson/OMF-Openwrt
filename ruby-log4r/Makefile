include $(TOPDIR)/rules.mk

PKG_NAME:=ruby-log4r
PKG_VERSION:=1.1.9
PKG_RELEASE:=3

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=master
PKG_SOURCE_URL:=https://github.com/colbygk/log4r.git
PKG_SOURCE_SUBDIR:=log4r
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)
# Tries to download from openwrt => obviously this does not work, 
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

RUBY_LIB_VER:=1.9

include $(INCLUDE_DIR)/package.mk

define Package/ruby-log4r/Default
  SUBMENU:=Ruby
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Ruby scripting language
  URL:=http://www.ruby-lang.org/
  DEFAULT:=y
  TITLE:=ruby-log4r
  DEPENDS+= ruby
endef

define Package/ruby-log4r/Default/description
Log4r is a comprehensive and flexible logging library written in Ruby for use in Ruby programs. It features a hierarchical logging system of any number of levels, custom level names, logger inheritance, multiple output destinations, execution tracing, custom formatting, thread safteyness, XML and YAML configuration, and more. 
endef

define Package/ruby-log4r
$(call Package/ruby-log4r/Default)
  TITLE+=Log4r
  DEPENDS+= +ruby
endef

define Package/ruby-log4r/description
$(call Package/ruby-log4r/Default/description)
endef

define Build/Compile
	# Nothing to build, its ruby!!
endef

define Package/ruby-log4r/install
	$(INSTALL_DIR) $(1)/usr/lib/ruby/$(RUBY_LIB_VER)/
	$(CP) $(PKG_BUILD_DIR)/lib/log4r $(1)/usr/lib/ruby/$(RUBY_LIB_VER)/
	$(CP) $(PKG_BUILD_DIR)/lib/log4r.rb $(1)/usr/lib/ruby/$(RUBY_LIB_VER)/
endef

$(eval $(call BuildPackage,ruby-log4r))
