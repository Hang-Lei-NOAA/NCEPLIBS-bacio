# src/Makefile.  Generated from Makefile.in by configure.

# src/ level makefile template

# Package-specific substitution variables
package   = nceplibs bacio
version   = v2.1.0
tarname   = bacio
precision = 4
distdir   = $(tarname)_$(version)_$(precision)

# Prefix-specific substitution variables
prefix = /home/Hang.Lei/save/library/NCEPLIBS-bacio

# Mixed package and prefix substitution variables
installdir = $(prefix)/$(distdir)

# Tool-specific substitution variables
FC      = ifort
FCFLAGS =   -O3  -xHOST  -traceback -FR -c
CC      = icc
CFLAGS  =   -O3  -DUNDERSCORE  -DLINUX -c
AR      = ar
ARFLAGS = crvs
RANLIB  = ranlib
INSTALL      = /bin/install -c
INSTALL_DATA = ${INSTALL} -m 644

# The library name
LIBRARY = lib$(tarname).a

# The file definitions. This include must occur before targets.
include make.filelist

# The targets
all: library

$(LIBRARY): $(OBJ_FILES)
	$(AR) $(ARFLAGS) $@ $(OBJ_FILES)
	$(RANLIB) $@

library: $(LIBRARY)

clean:
	cd test && $(MAKE) $@
	-rm *.o *.mod *.a 2>/dev/null

distclean:
	cd test && $(MAKE) $@
	-rm *.o *.mod *.a 2>/dev/null
	-rm Makefile 2>/dev/null

check: library
	cd test && $(MAKE) $@

# ...Gnu-style installation
install:
	$(INSTALL) -d $(DESTDIR)$(installdir)/include
	$(INSTALL_DATA) *.mod $(DESTDIR)$(installdir)/include
	$(INSTALL) -d $(DESTDIR)$(installdir)/lib
	$(INSTALL_DATA) $(LIBRARY) $(DESTDIR)$(installdir)/lib
	$(INSTALL_DATA) ../config.log $(DESTDIR)$(installdir)

# ...NCO-style installation
nco_install: FORCE
	$(INSTALL) -d $(DESTDIR)$(installdir)
	$(INSTALL_DATA) $(LIBRARY) $(DESTDIR)$(installdir)/lib$(distdir).a
	$(INSTALL) -d $(DESTDIR)$(installdir)/incmod/$(distdir)
	$(INSTALL_DATA) *.mod $(DESTDIR)$(installdir)/incmod/$(distdir)
	$(INSTALL_DATA) ../config.log $(DESTDIR)$(installdir)/config.log.$(distdir)

FORCE:
	@if [ -d $(DESTDIR)$(installdir) ]; then \
          echo; \
	  echo "*** NCO-style installation does not install into existing directories! ***"; \
	  echo "*** $(DESTDIR)$(installdir) already exists! ***"; \
          echo; \
	  exit 1; \
	fi

# ...Universal uninstallation
uninstall:
	-rm -fr $(DESTDIR)$(installdir) >/dev/null 2>&1

# ...Reconfig targets
Makefile: Makefile.in ../config.status
	cd .. && ./config.status src/$@

../config.status: ../configure
	cd .. && ./config.status --recheck

# Specify targets that do not generate filesystem objects
.PHONY: all clean distclean check install nco_install uninstall

# Dependency include file
include make.dependencies

# Suffix rules
.SUFFIXES:
.SUFFIXES: .f .c .o
.f.o:
	$(FC) $(FCFLAGS) $<

.c.o:
	$(CC) $(CFLAGS) $<

