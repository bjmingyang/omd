include ../../Makefile.omd

NAME        = histou
VERSION     = 0.4.1
SRC         = $(NAME)-$(VERSION).tar.gz
PWD         = $(shell pwd)

.PHONY: skel

build:

install:
	tar zxf $(SRC) -C $(DESTDIR)$(OMD_ROOT)/share --exclude=histou.js
	sed -i s/'\x27histou.ini'/\$$_SERVER[\'OMD_ROOT\'].\'"\/etc\/histou\/histou.ini"/ $(DESTDIR)$(OMD_ROOT)/share/histou/index.php
	sed -i s/'\x27histou.ini'/\$$_SERVER[\'OMD_ROOT\'].\'"\/etc\/histou\/histou.ini"/ $(DESTDIR)$(OMD_ROOT)/share/histou/rule_examinant.php
	cp omd-histou.js $(DESTDIR)$(OMD_ROOT)/share/grafana/public/dashboards/histou.js
	rm -rf histou

skel:
	sed -i 's#phpCommand = .*#phpCommand = "$(PHP_FCGI_BIN)"#' $(SKEL)/etc/histou/histou.ini

clean:
	rm -rf histou

package:
	git clone  --depth=1 --branch "v$(VERSION)" https://github.com/Griesbacher/histou
	tar zcf $(SRC) histou --exclude=.git --exclude=histou/tests --exclude=histou/conf --exclude=histou/stylecheck.sh
	sed  "s#var url = 'http://localhost/histou/';#var site = window.location.href.match(/(https?:\\\\/\\\\/.*?\\\\/.*?)\\\\/grafana\\\\/.*/);\n    if(site \&\& site.length > 1){\n        url = site[1]+'/histou/';\n    }#" histou/histou.js > omd-histou.js
	rm -rf histou
