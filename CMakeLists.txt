# MQ2DamageMeter
# Forked from RedGuides/MQ2DamageMeter (github.com/RedGuides org sweep, forum-plugins-2026-08-02
# follow-up batch). Vendored as a git submodule tracking https://github.com/blbruegg/MQ2DamageMeter
# (fork of RedGuides/MQ2DamageMeter). See F:\\EQProject\\docs\\re_progress.md for the write-up.
#
# Has a real external dependency declared in this directory's vcpkg_mq.txt (sqlite3) --
# this project's vcpkg_manifest.cmake auto-discovers that file at configure time.
#

include("../../Plugin.cmake")

find_package(unofficial-sqlite3 CONFIG REQUIRED)

set(MQ2DamageMeter_SOURCES
    "MQ2DamageMeter.cpp"
)

source_groups("Source Files" ${MQ2DamageMeter_SOURCES})

add_library(MQ2DamageMeter SHARED
    ${MQ2DamageMeter_SOURCES}
)

set_target_properties(MQ2DamageMeter PROPERTIES FOLDER "core/plugins")

target_Plugin_props(MQ2DamageMeter)

target_link_libraries(MQ2DamageMeter PRIVATE MQ2Main
    unofficial::sqlite3::sqlite3)
