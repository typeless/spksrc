PKG_NAME = gitea
PKG_VERS = 1.8
PKG_EXT = tar.gz
PKG_DIST_NAME = $(PKG_NAME)-$(PKG_VERS).$(PKG_EXT)
PKG_DIST_SITE = https://github.com/go-gitea/gitea/raw/master
PKG_DIR = $(PKG_NAME)-$(PKG_VERS)

DEPENDS = cross/git

HOMEPAGE = https://gitea.io
COMMENT  = Git with a cup of tea, painless self-hosted git service
LICENSE  = MIT

COPY_TARGET = gitea_copy

# Define GO_ARCH as per golang standards
ifeq ($(findstring $(ARCH),$(ARM5_ARCHES)),$(ARCH))
GO_ARCH = arm
ENV += GOARM=5
endif
ifeq ($(findstring $(ARCH),$(ARM7_ARCHES)),$(ARCH))
GO_ARCH = arm
ENV += GOARM=7
endif
ifeq ($(findstring $(ARCH),$(ARM8_ARCHES)),$(ARCH))
GO_ARCH = arm64
endif
ifeq ($(findstring $(ARCH),$(x86_ARCHES)),$(ARCH))
GO_ARCH = 386
endif
ifeq ($(findstring $(ARCH),$(x64_ARCHES)),$(ARCH))
GO_ARCH = amd64
endif

ifeq ($(GO_ARCH),)
$(error Unsupported ARCH $(ARCH))
endif
ENV += GOARCH=$(GO_ARCH)


include ../../mk/spksrc.spk.mk

include ../../mk/spksrc.download.mk
checksum: download
include ../../mk/spksrc.checksum.mk
extract: checksum
include ../../mk/spksrc.extract.mk

.PHONY: gitea_copy

gitea_copy: extract $(WORK_DIR)/config
	install -m 755 -d $(STAGING_DIR)/$(DSM_UI_DIR)
	cp PLIST $(INSTALL_PLIST)
	(cd $(WORK_DIR)/$(PKG_DIR) && tar cpf - `cat $(INSTALL_PLIST) | cut -d':' -f2` | \
	  tar xpf - -C $(STAGING_DIR)/$(DSM_UI_DIR))
