include ../../../Makefile.omd

NAME        = check_nsc_web
VERSION     = 0.4.1
SRC         = $(NAME)-$(VERSION).tar.gz
GOPKG       = 1.7
GOVERSION   = $(shell grep ^VERSION ../../go-${GOPKG}/Makefile | awk '{ print $$3 }')
GOPATH      = go
PWD         = $(shell pwd)
#BRANCH      = v$(VERSION)
GITURL      = github.com/m-kraus
BRANCH      = v0.4.1

.PHONY: skel

build:
	tar zxf $(SRC)
	export GOROOT=$(PWD)/../../go-$(GOPKG)/go-$(GOVERSION)/ && export GOPATH=$(PWD)/$(GOPATH)/ && PATH=$$GOROOT/bin:$$PATH && \
	CGO_ENABLED=0 go build $(NAME).go

install:
	mkdir -p $(DESTDIR)$(OMD_ROOT)/lib/nagios/plugins
	install -m 755 $(PWD)/$(NAME) $(DESTDIR)$(OMD_ROOT)/lib/nagios/plugins

skel:

clean:
	rm -f $(NAME)
	rm -f $(NAME).go
	rm -rf $(GOPATH)

package: clean
	mkdir -p $(GOPATH)
	export GOROOT=$(PWD)/../go-$(GOPKG)/go-$(GOVERSION)/ && export GOPATH=$(PWD)/$(GOPATH)/ && PATH=$$GOROOT/bin:$$PATH && \
		mkdir -p $(GOPATH)/src/$(GITURL) && \
		cd $(GOPATH)/src/$(GITURL) && \
		git clone --depth=1 --branch "$(BRANCH)" https://$(GITURL)/$(NAME) && \
		cd $(NAME) && \
		tar zcf $(PWD)/$(SRC) $(NAME).go

