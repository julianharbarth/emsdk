cmake_minimum_required(VERSION 3.19)

if (NOT EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/upstream/emscripten/emcc)
    set(emsdk-command-path ${CMAKE_CURRENT_SOURCE_DIR}/emsdk)
    if(WIN32)
        cmake_path(NATIVE_PATH emsdk-command-path NORMALIZE native-emsdk-command-path)
        execute_process(COMMAND cmd /c ${native-emsdk-command-path} install 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY
            )

        execute_process(COMMAND cmd /c ${native-emsdk-command-path} activate 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY
            ) 
    else()
        execute_process(COMMAND ${emsdk-command-path} install 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY
            )

        execute_process(COMMAND ${emsdk-command-path} activate 3.1.10
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            COMMAND_ECHO STDOUT
            COMMAND_ERROR_IS_FATAL ANY
            )
    endif()
endif ()
