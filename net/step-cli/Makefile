# SPDX-License-Identifier: GPL-2.0-or-later

include $(TOPDIR)/rules.mk

PKG_NAME:=step-cli
PKG_VERSION:=0.26.0
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/cli-$(PKG_VERSION)
PKG_SOURCE:=step_$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/smallstep/cli/releases/download/v$(PKG_VERSION)
PKG_HASH:=128cebf24a3043ef1616be47d07c95f8a0d3432b626ff060c69eb1c806e98614

PKG_MAINTAINER:=Magnus Kroken <mkroken@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/smallstep/cli/cmd/step
GO_PKG_LDFLAGS_X:=main.version=$(PKG_VERSION)
GO_PKG_INSTALL_BIN_PATH:=/usr/sbin

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/step-cli
	SECTION:=net
	CATEGORY:=Network
	TITLE:=CLI tool for public key infrastructure
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/step-cli/description
	step is an easy-to-use CLI tool for building, operating, and automating Public Key Infrastructure (PKI) systems and workflows. It's the client counterpart to the step-ca online Certificate Authority (CA).
You can use it for many common crypto and X.509 operations - either independently, or with an online CA.
endef

define Package/step-cli/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/step $(1)/usr/sbin
endef

define GoPackage/Package/Install/Src
endef

$(eval $(call GoBinPackage,step-cli))
$(eval $(call BuildPackage,step-cli))
