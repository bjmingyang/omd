include ../../Makefile.omd

NAME=coshsh
VERSION=3.4.3.1
COSHSH=$(NAME)-$(VERSION)

build:
	tar xvzf $(COSHSH).tar.gz
	cd $(COSHSH) && \
	    export PYTHONPATH=$$PYTHONPATH:$(DESTDIR)$(OMD_ROOT)/lib/python ; \
	    python setup.py build

install:
	mkdir -p $(DESTDIR)$(OMD_ROOT)/bin
	mkdir -p $(DESTDIR)$(OMD_ROOT)/lib/python
	mkdir -p $(DESTDIR)$(OMD_ROOT)/share/coshsh
	mkdir -p $(DESTDIR)$(OMD_ROOT)/var/coshsh
	cd $(COSHSH) && \
	    export PYTHONPATH=$$PYTHONPATH:$(DESTDIR)$(OMD_ROOT)/lib/python ; \
	    python setup.py install \
	        --prefix= \
	        --home=$(DESTDIR)$(OMD_ROOT) \
                --install-platlib=$(DESTDIR)$(OMD_ROOT)/lib/python \
                --install-purelib=$(DESTDIR)$(OMD_ROOT)/lib/python \
                --install-scripts=$(DESTDIR)$(OMD_ROOT)/bin \
                --install-data=$(DESTDIR)$(OMD_ROOT)/share/coshsh
	cp datasource_snmptt.py \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/classes
	cp datarecipient_atomic.py \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/classes
	cp app_snmptrapdlog.py \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/classes
	cp app_snmptrapdlog_default.tpl \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/templates
	cp common_traps.tpl \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/templates
	cp check_logfiles_snmptt.tpl \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/templates
	cp HostSNMPTrapinfo.tpl \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/recipes/default/templates
	cp check_git_updates \
	    $(DESTDIR)$(OMD_ROOT)/bin
	chmod 755 $(DESTDIR)$(OMD_ROOT)/bin/check_git_updates
	mkdir -p $(DESTDIR)$(OMD_ROOT)/share/coshsh/contrib
	cp coshsh-prepare-landscape \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/contrib
	cp consol_commands.cfg \
	    $(DESTDIR)$(OMD_ROOT)/share/coshsh/contrib


skel:

clean:
	rm -rf $(COSHSH)
