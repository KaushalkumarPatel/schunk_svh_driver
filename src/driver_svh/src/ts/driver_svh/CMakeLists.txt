# this is for emacs file handling -*- mode: cmake; indent-tabs-mode: nil -*-
ICMAKER_SET("ts_SVHDriver" IDE_FOLDER ${DRIVER_SVH_IDE_FOLDER})

ICMAKER_ADD_SOURCES(
  ts_main.cpp
  ts_SVHDriver.cpp
  )

IF(Boost_FOUND)
  IF(BUILD_SHARED_LIBS)
    ICMAKER_LOCAL_CPPDEFINES("-DBOOST_TEST_DYN_LINK")
  ENDIF(BUILD_SHARED_LIBS)
ENDIF(Boost_FOUND)

ICMAKER_INCLUDE_DIRECTORIES( ${DRIVER_SVH_INCLUDE_DIRS} )

ICMAKER_EXTERNAL_DEPENDENCIES(
  Boost_UNIT_TEST_FRAMEWORK
  )

ICMAKER_INTERNAL_DEPENDENCIES(
  driver_svh
  icl_core
  icl_comm
  Boost_THREAD
  )

ICMAKER_BUILD_TEST()
