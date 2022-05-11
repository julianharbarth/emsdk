cmake_minimum_required(VERSION 3.19)

if (NOT EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/upstream/emscripten/emcc)
    execute_process(COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/emsdk install 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY)

    execute_process(COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/emsdk activate 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY)
endif ()
