SHELL=/bin/sh
CLASS=W
VERSION=
SFILE=config/suite.def

default: header
	@ sys/print_instructions

CG_csr: cg_csr		       
cg_csr: header	       
	cd CG_csr; $(MAKE) CLASS=$(CLASS)

CG_coo: cg_coo		       
cg_coo: header	       
	cd CG_coo; $(MAKE) CLASS=$(CLASS)

CG_dense: cg_dense		       
cg_dense: header	       
	cd CG_dense; $(MAKE) CLASS=$(CLASS)

# Awk script courtesy cmg@cray.com, modified by Haoqiang Jin
suite:
	@ awk -f sys/suite.awk SMAKE=$(MAKE) $(SFILE) | $(SHELL)


# It would be nice to make clean in each subdirectory (the targets
# are defined) but on a really clean system this will won't work
# because those makefiles need config/make.def
clean:
	- rm -f core *~ */core */*~
	- rm -f */*.o */*.obj */*.exe */*.mod */npbparams.h */blk_par.h
	- rm -f sys/setparams sys/makesuite sys/setparams.h
	- rm -rf */rii_files

veryclean: clean
	- rm -f config/make.def config/suite.def 
	- rm -f bin/cg_csr.* bin/cg_coo.* bin/cg_dense.*

header:
	@ sys/print_header



