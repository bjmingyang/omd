include ../../Makefile.omd

SAMPLICATOR=samplicator-f4ba263

build:
	tar xvzf $(SAMPLICATOR).tar.gz
	cd $(SAMPLICATOR) && \
	    ./autogen.sh; \
	    ./configure; \
	    make; \
	    strip samplicate

install:
	mkdir -p $(DESTDIR)$(OMD_ROOT)/bin
	cp snmptrap_logger.sh \
	    $(DESTDIR)$(OMD_ROOT)/bin
	cp $(SAMPLICATOR)/samplicate $(DESTDIR)$(OMD_ROOT)/bin
	# missing: samplicate init-script
	# missing: samplicate cronjob which restarts on site changes
	# SNMPTRAPD hook
	cp samplicate_watch $(DESTDIR)$(OMD_ROOT)/bin
	chmod 755 $(DESTDIR)$(OMD_ROOT)/bin/samplicate_watch
	mkdir -p $(DESTDIR)$(OMD_ROOT)/share/samplicate
	cp samplicate.service $(DESTDIR)$(OMD_ROOT)/share/samplicate
	cp samplicate_watch.service $(DESTDIR)$(OMD_ROOT)/share/samplicate
	cp README.systemd $(DESTDIR)$(OMD_ROOT)/share/samplicate

skel:

clean:
	rm -rf $(SAMPLICATOR)
