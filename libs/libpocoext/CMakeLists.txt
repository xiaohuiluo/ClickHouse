add_library (pocoext ${LINK_MODE}
    src/LevelFilterChannel.cpp
    src/ThreadNumber.cpp
    src/SessionPoolHelpers.cpp

    include/Poco/Ext/LevelFilterChannel.h
    include/Poco/Ext/ThreadNumber.h
    include/Poco/Ext/SessionPoolHelpers.h)

if (Poco_Data_FOUND)
    target_include_directories (pocoext SYSTEM PRIVATE ${Poco_Data_INCLUDE_DIR})
    target_link_libraries(pocoext PRIVATE ${Poco_Data_LIBRARY})
endif()

target_include_directories (pocoext PUBLIC include PRIVATE ${COMMON_INCLUDE_DIR})

if (NOT USE_INTERNAL_POCO_LIBRARY)
    target_include_directories (pocoext SYSTEM BEFORE PUBLIC ${Poco_INCLUDE_DIRS})
endif ()

target_link_libraries(pocoext PUBLIC ${Poco_Foundation_LIBRARY})
