include $(TOPDIR)/rules.mk

PKG_NAME:=gluon-fffd-migrator
PKG_VERSION:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/gluon-fffd-migrator
  SECTION:=gluon
  CATEGORY:=Gluon
  TITLE:=timed migration for mesh-breaking config changes
  DEPENDS:=+gluon-core gluon-autoupdater
endef

define Package/gluon-fffd-migrator/description
	Executes migration scripts at specified times.

	Mesh-breaking changes must be done at a specific time on all nodes. This
	module allows to specify scripts which are executed at a given point in time
	(or right after that time).

	Migrations are defined in the 'migrations' folder in the gluon 'site'
	directory. The files in the folder must have the executable bit set and the
	filename must have the following pattern 'YYYY-MM-DD-ID' whereas the ID can
	be an arbitrary string.

	The migration tool ensures that each migration is executed only once.

	To ensure that old migrations are applied to fresh installations, the
	migrations are executed as part of the upgrade process.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/gluon-fffd-migrator/install
	cp -fpR ./files/* $(1)/

	mkdir -p $(1)/lib/gluon/migrations
	cp -fpR $(GLUON_SITEDIR)/migrations/[[:digit:]][[:digit:]][[:digit:]][[:digit:]]-[[:digit:]][[:digit:]]-[[:digit:]][[:digit:]]-* $(1)/lib/gluon/migrations
endef

define Package/gluon-fffd-migrator/postinst
endef

$(eval $(call BuildPackage,gluon-fffd-migrator))

