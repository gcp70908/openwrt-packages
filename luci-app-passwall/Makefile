# Copyright (C) 2018-2020 L-WRT Team
# Copyright (C) 2021 xiaorouji
#
# This is free software, licensed under the GNU General Public License v3.

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-passwall
PKG_VERSION:=4.36
PKG_RELEASE:=1
#20210928

PKG_CONFIG_DEPENDS:= \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Trojan_Plus \

LUCI_TITLE:=LuCI support for PassWall
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+coreutils +coreutils-base64 +coreutils-nohup +curl \
	+dnsmasq-full +dns2socks +ipset +ip-full +ipt2socks +iptables-mod-tproxy \
	+libuci-lua +lua +luci-lib-jsonc +microsocks +tcping +resolveip \
	+unzip \
	+PACKAGE_$(PKG_NAME)_INCLUDE_PDNSD:pdnsd-alt \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Trojan_Plus:trojan-plus \

define Package/$(PKG_NAME)/config
menu "Configuration"

config PACKAGE_$(PKG_NAME)_INCLUDE_PDNSD
	bool "Include PDNSD"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_Trojan_Plus
	bool "Include Trojan-Plus"
	default y

endmenu
endef

define Package/$(PKG_NAME)/conffiles
/etc/config/passwall
/etc/config/passwall_server
/usr/share/passwall/rules/direct_host
/usr/share/passwall/rules/direct_ip
/usr/share/passwall/rules/proxy_host
/usr/share/passwall/rules/proxy_ip
/usr/share/passwall/rules/block_host
/usr/share/passwall/rules/block_ip
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
