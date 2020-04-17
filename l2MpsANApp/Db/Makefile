TOP=../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

# ==========================================
# MPS LN specific databases
# ==========================================
DB += mpsAN.db
# ==========================================

# For saving and loading yaml configuration
DB += saveLoadConfig.db

# Install Common databases needed by All IOCs
# ========================================================
# Install databases from iocAdmin package
# These databases support IOC Health and Monitoring
# ========================================================
DB_INSTALLS += $(IOCADMIN)/db/iocAdminSoft.db
DB_INSTALLS += $(IOCADMIN)/db/iocAdminScanMon.db
IOCRELEASE_DB += iocRelease.db

# Install Database to support reading the status of the autosave package:
DB_INSTALLS += $(AUTOSAVE)/db/save_restoreStatus.db

# Install Database for tprTrigger module
DB_INSTALLS += $(TPRTRIGGER)/db/tprTrig.db
DB_INSTALLS += $(TPRTRIGGER)/db/tprDeviceNamePV.db

# Install Databse for tprPattern module
DB_INSTALLS += $(TPRPATTERN)/db/tprPattern.db

# Install Database for the evrClient module
DB_INSTALLS += $(EVRCLIENT)/db/evr.db
DB_INSTALLS += $(EVRCLIENT)/db/evrEventCtrl.db
DB_INSTALLS += $(EVRCLIENT)/db/evrPatternAll.db
DB_INSTALLS += $(EVRCLIENT)/db/evrEventAll.db
DB_INSTALLS += $(EVRCLIENT)/db/evrDevTrig.db
DB_INSTALLS += $(EVRCLIENT)/db/bsaATTREdef.db

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

