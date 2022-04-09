# simple install makefile
#

SBINDIR := /usr/local/sbin
UNITDIR := /etc/systemd/system

default:
	@echo
	@echo "use 'make install' to install to $(UNITDIR) and $(SBINDIR)"
	@echo "you can override these with SBINDIR= and UNITDIR= variables"
	@echo

install:
	install -p -m 0755 -D obsworker-watch $(DESTDIR)$(SBINDIR)/obsworker-watch
	install -p -m 0644 -D obsworker-watch.socket $(DESTDIR)$(UNITDIR)/obsworker-watch.socket
	install -p -m 0644 -D obsworker-watch@.service $(DESTDIR)$(UNITDIR)/obsworker-watch@.service
	@if [ -z "$(DESTDIR)" ]; then \
		echo; echo "enable with 'systemd daemon-reload; systemctl enable --now obsworker-watch.socket"; echo;\
	fi

enable:
	systemctl daemon-reload
	systemctl enable --now obsworker-watch.socket
