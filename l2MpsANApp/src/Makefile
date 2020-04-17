TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================
USR_CXXFLAGS += -std=c++0x

# =====================================================
# Path to "NON EPICS" External PACKAGES: USER INCLUDES
# ======================================================
USR_INCLUDES = $(addprefix -I,$(BOOST_INCLUDE) $(CPSW_FRAMEWORK_INCLUDE) $(YAML_INCLUDE) $(L2MPS_INCLUDE) $(YAMLREADER_INCLUDE) $(DEVICELIB_INCLUDE))
# =====================================================

# ======================================================
#PATH TO "NON EPICS" EXTERNAL PACKAGES: USER LIBRARIES
# ======================================================
cpsw_DIR = $(CPSW_FRAMEWORK_LIB)
yaml-cpp_DIR = $(YAML_LIB)
l2Mps_DIR = $(L2MPS_LIB)
deviceLib_DIR = $(DEVICELIB_LIB)
yamlReader_DIR  = $(YAMLREADER_LIB)
hpstpr_DIR = $(HPSTPR_LIB)

# =====================================================

# ======================================================
# LINK "NON EPICS" EXTERNAL PACKAGE LIBRARIES STATICALLY
# =======================================================
USR_LIBS_Linux += l2Mps yamlReader deviceLib hpstpr cpsw yaml-cpp
# ======================================================

#=============================
# Build the IOC application

PROD_IOC = l2MpsAN
# l2MpsAN.dbd will be created and installed
DBD += l2MpsAN.dbd

# l2MpsAN.dbd will be made up from these files:
l2MpsAN_DBD += base.dbd
l2MpsAN_DBD += devIocStats.dbd
l2MpsAN_DBD += asSupport.dbd
l2MpsAN_DBD += l2mps_l1bsa.dbd

# Include dbd files from all support applications:
l2MpsAN_DBD += system.dbd
l2MpsAN_DBD += asyn.dbd
l2MpsAN_DBD += l2MpsAsyn.dbd
l2MpsAN_DBD += yamlLoader.dbd
l2MpsAN_DBD += ycpswasyn.dbd
l2MpsAN_DBD += yamlDownloader.dbd
l2MpsAN_DBD += tprTriggerAsynDriver.dbd
l2MpsAN_DBD += tprPatternAsynDriver.dbd
l2MpsAN_DBD += bsaCore.dbd
l2MpsAN_DBD += bsa.dbd
l2MpsAN_DBD += iocAdmin.dbd

# Add all the support libraries needed by this IOC
l2MpsAN_LIBS += devIocStats
l2MpsAN_LIBS += autosave
l2MpsAN_LIBS += yamlLoader
l2MpsAN_LIBS += l2MpsAsyn
l2MpsAN_LIBS += yamlDownloader
l2MpsAN_LIBS += ycpswasyn
l2MpsAN_LIBS += eventBsaSupport
l2MpsAN_LIBS += tprPattern
l2MpsAN_LIBS += tprTrigger
l2MpsAN_LIBS += BsaCore
l2MpsAN_LIBS += asyn

# Link QSRV (pvAccess Server) if available
ifdef EPICS_QSRV_MAJOR_VERSION
   l2MpsAN_LIBS += qsrv
   l2MpsAN_LIBS += $(EPICS_BASE_PVA_CORE_LIBS)
   l2MpsAN_DBD  += PVAServerRegister.dbd
   l2MpsAN_DBD  += qsrv.dbd
endif

# l2MpsAN_registerRecordDeviceDriver.cpp derives from l2MpsAN.dbd
l2MpsAN_SRCS += l2MpsAN_registerRecordDeviceDriver.cpp
l2MpsAN_SRCS += l2mps_l1bsa l2mps_l1bsa_channels

# Build the main IOC entry point on workstation OSs.
l2MpsAN_SRCS_DEFAULT += l2MpsANMain.cpp
l2MpsAN_SRCS_vxWorks += -nil-


# Add support from base/src/vxWorks if needed
#l2MpsAN_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

# Finally link to the EPICS Base libraries
l2MpsAN_LIBS += $(EPICS_BASE_IOC_LIBS)

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

