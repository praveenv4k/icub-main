# Copyright: (C) 2012 RobotCub Consortium
# Authors: Alberto Cardellino
# CopyPolicy: Released under the terms of the GNU GPL v2.0.

PREPARE_DEVICE(embObjMotionControl TYPE embObjMotionControl
    INCLUDE embObjMotionControl.h
    WRAPPER controlboard)

 IF (NOT SKIP_embObjMotionControl)
  set(ICUB_COMPILE_EMBOBJ_LIBRARY ON CACHE INTERNAL "use the embObjLib lib")
  INCLUDE(../embObjLib/embObjLib.cmake)
  INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR} ${YARP_INCLUDE_DIRS} ${iCubDev_INCLUDE_DIRS} )

#    ADD_LIBRARY(embObjMotionControl embObjMotionControl.cpp embObjMotionControl.h usrcbk/eOcfg_nvsEP_mc_usrcbk_pippo.c )
    ADD_LIBRARY(embObjMotionControl embObjMotionControl.cpp embObjMotionControl.h)
    TARGET_LINK_LIBRARIES(embObjMotionControl debugStream ethResources iCubDev ${YARP_LIBRARIES} ${ACE_LIBRARIES})
    icub_export_library(embObjMotionControl)
ENDIF (NOT SKIP_embObjMotionControl)

