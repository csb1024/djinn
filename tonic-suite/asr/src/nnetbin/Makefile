COMMON=../../../../common/

include $(COMMON)/Makefile.config

all:
EXTRA_CXXFLAGS = -Wno-sign-compare \
								 -O3 \
								 -fpermissive \
								 -I$(COMMON)/include \
								 -I$(CAFFE)/include \
								 -I$(CUDA)/include 

ifeq ($(CPU_ONLY), 1)
	EXTRA_CXXFLAGS   += -DCPU_ONLY
endif

include ../kaldi.mk

LDFLAGS += $(CUDA_LDFLAGS)
LDLIBS += $(CUDA_LDLIBS) $(COMMON)/libtonic.a \
					$(CAFFE)/lib/libcaffe.so \
					-lglog


BINFILES = nnet-train-frmshuff \
        nnet-train-perutt \
        nnet-train-mmi-sequential \
        nnet-train-mpe-sequential \
        rbm-train-cd1-frmshuff rbm-convert-to-nnet \
        nnet-forward nnet-copy nnet-info nnet-concat \
        transf-to-nnet cmvn-to-nnet nnet-initialize \
        nnet-kl-hmm-acc nnet-kl-hmm-mat-to-component 

TESTFILES = 

ADDLIBS = ../nnet/kaldi-nnet.a ../cudamatrix/kaldi-cudamatrix.a ../lat/kaldi-lat.a \
          ../hmm/kaldi-hmm.a ../tree/kaldi-tree.a ../matrix/kaldi-matrix.a \
          ../util/kaldi-util.a ../base/kaldi-base.a

include ../makefiles/default_rules.mk
