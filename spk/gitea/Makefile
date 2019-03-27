SPK_NAME = Gitea
SPK_VERS = 1.8
SPK_REV = rc-1
SPK_ICON = src/gitea.png

DEPENDS = cross/gitea

MAINTAINER = Gitea Authors
DESCRIPTION = Git with a cup of tea, painless self-hosted git service
RELOAD_UI = yes
STARTABLE = yes
DISPLAY_NAME = Gitea
CHANGELOG = ""

HOMEPAGE = https://gitea.io
LICENSE  = MIT

SERVICE_USER = auto
SERVICE_SETUP = src/service-setup.sh
SERVICE_PORT = 3000
SERVICE_PORT_TITLE = $(DISPLAY_NAME)

# Admin link for in DSM UI
ADMIN_PORT = $(SERVICE_PORT)

include ../../mk/spksrc.spk.mk
