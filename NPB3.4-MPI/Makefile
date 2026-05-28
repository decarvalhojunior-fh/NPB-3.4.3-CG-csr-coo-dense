SHELL=/bin/sh
CLASS=U
SUBTYPE=
VERSION=
F08=def
MFLAGS=CLASS=$(CLASS) F08=$(F08)
SFILE=config/suite.def

default: header
	@ sys/print_instructions

CG_csr: cg_csr
cg_csr: header
	cd CG_csr; $(MAKE) $(MFLAGS)

CG_csr_p2p: cg_csr_p2p
cg_csr_p2p: header
	cd CG_csr_p2p; $(MAKE) $(MFLAGS)

CG_coo: cg_coo
cg_coo: header
	cd CG_coo; $(MAKE) $(MFLAGS)

CG_dense: cg_dense
cg_dense: header
	cd CG_dense; $(MAKE) $(MFLAGS)


# Awk script courtesy cmg@cray.com, modified by Haoqiang Jin
suite:
	@ awk -f sys/suite.awk SMAKE=$(MAKE) $(SFILE) | $(SHELL)


# It would be nice to make clean in each subdirectory (the targets
# are defined) but on a really clean system this will won't work
# because those makefiles need config/make.def
clean:
	- rm -f core *~ */core */*~
	- rm -f */*.o */*.mod */*.obj */*.exe */npbparams.h */mpinpb.*
	- rm -f MPI_dummy/test MPI_dummy/libmpi.a
	- rm -f sys/setparams sys/makesuite sys/setparams.h
	- rm -f btio.*.out*

veryclean: clean
	- rm -f config/make.def config/suite.def 
	- rm -f bin/cg_csr.* bin/cg_csr_p2p.* bin/cg_coo.* bin/cg_dense.*

header:
	@ sys/print_header
