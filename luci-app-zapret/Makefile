#
# Copyright (c) 2024 remittor
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-farewelldpi
PKG_VERSION:=71.20250708
PKG_LICENSE:=MIT
PKG_MAINTAINER:=ardemanse <https://github.com/ardemanse>

LUCI_TITLE:=LuCI control panel for Zapret
LUCI_DEPENDS:=+zapret
LUCI_PKGARCH:=all

define Package/$(PKG_NAME)/postinst
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
	rm -f /tmp/luci-index*
	rm -rf /tmp/luci-modulecache/
	#killall -HUP rpcd 2>/dev/null
	/etc/init.d/rpcd reload
	[ -f "/sbin/luci-reload" ] && /sbin/luci-reload
	[ -f "/etc/init.d/uhttpd" ] && /etc/init.d/uhttpd reload
fi
exit 0
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
