```
expdp app_prd/Bonyan123@APEX content=METADATA_ONLY schemas=APP_PRD directory=EXP_DIR  dumpfile=APP_PRD_metadata_14000204.dmp logfile=expdp_APP_PRD_metadata_14000204.log

impdp app_dev/Bonyan123@localhost:1521/APEXPDB TABLE_EXISTS_ACTION=REPLACE DIRECTORY=EXP_DIR DUMPFILE=APP_PRD_metadata_14000204.dmp REMAP_SCHEMA=APP_PRD:APP_DEV REMAP_TABLESPACE=TBS_PRD_01:TBS_DEV_01
```