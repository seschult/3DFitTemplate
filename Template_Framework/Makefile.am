AUTOMAKE_OPTIONS = subdir-objects check-news gnu

AM_CFLAGS =  -g 
# -Wno-long-long -Wall -Wextra   -Werror -pedantic -Wno-error=long-long 
AM_CXXFLAGS = -g 
#-Wno-long-long -Wall -Wextra   -Werror -pedantic -Wno-error=long-long 


ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS} -I m4
AM_CPPFLAGS = -Ilib -I$(top_srcdir)/lib -Isrc -I$(top_srcdir)/src -ITool


ROOTMAP_LIB_SO =




AM_CFLAGS+=$(ROOT_CFLAGS)
AM_CPPFLAGS+=$(ROOT_CFLAGS)
LIBS+=$(ROOT_LIBS)
ROOTMAP_LIB_SO+=libMinuit.so libMLP.so libMatrix.so libTree.so libGraf.so libTreePlayer.so libProof.so libXMLIO.so


pkglib_LTLIBRARIES = libzbestlib.la libmtoplib.la

libzbestlib_la_SOURCES = src/ZBestNumber.cxx

libzbestlib_la_SOURCES+=gen/zbestlibDict.cxx 

########################################################################
libmtoplib_la_SOURCES = Code/mtop_fit.cxx

libmtoplib_la_SOURCES+=gen/mtopDict.cxx 
########################################################################


# -Bsp compile file with header
gen/mtopDict.cxx:  config.h  Code/mtop_fit.h    src/mtopLinkDef.h 
		rootcint -f  $@   -c  $(AM_CPPFLAGS)  -p $^   


gen/zbestlibDict.cxx:  config.h  src/ZBestNumber.h    src/zbestlibLinkDef.h 
		rootcint -f  $@   -c  $(AM_CPPFLAGS)  -p $^   


libzbestlib_la_LDFLAGS = -release $(EXAMPLE_API_VERSION)

zbestlib_includedir = $(includedir)/$(PACKAGE)
zbestlib_include_HEADERS =\
src/ZBestNumber.h\
src/ZROOT.h


libzbestlib_la_SOURCES+= src/zbestlibLinkDef.h


#######################################################################
libmtoplib_la_LDFLAGS = -release $(EXAMPLE_API_VERSION)

mtoplib_includedir = $(includedir)/$(PACKAGE)
mtoplib_include_HEADERS =\Code/mtop_fit.h\
src/ZROOT.h


libmtoplib_la_SOURCES+= src/mtopLinkDef.h
#######################################################################


bin_PROGRAMS = Fit3


test_CPPFLAGS=$(AM_CPPFLAGS)
test_CXXFLAGS=$(AM_CXXFLAGS)
test_CFLAGS=$(AM_CFLAGS)
test_SOURCES= src/test.cxx
test_LIBS= $(LIBS)
test_LDADD=libzbestlib.la

#tunning_SOURCES= Code/tunning.cxx 



#Fit_Class_SOURCES= Code/Fit_Class.cxx  

#Fit_Class2_SOURCES= Code/Fit_Class2.cxx

#Background1_SOURCES= Code/Background_1.cxx

#Par_SOURCES= Code/Fit_Par_Mass.cxx



#######################################################################
#Fit_Class3_SOURCES= Code/Fit_Class3.cxx
#Fit_Class3_LIBS= $(LIBS)
#Fit_Class3_LDADD=libmtoplib.la


#######################################################################



stupid_SOURCES= Code/RunParametrization.cxx Code/FCN.cxx Code/TemplateHolder.cxx Code/Fill3D.cxx
stupid_LIBS= $(LIBS)
stupid_LDADD=libmtoplib.la 
stupid_CXXFLAGS=-fopenmp
stupid_LDFLAGS=-fopenmp


 




all: all-am
