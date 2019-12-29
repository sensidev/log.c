project(log)

list(APPEND ${PROJECT_NAME}_SOURCES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/log.c
        )

add_library(${PROJECT_NAME} OBJECT EXCLUDE_FROM_ALL ${${PROJECT_NAME}_SOURCES})

if (DEFINED ${TARGET_MCU})
    target_compile_definitions(${PROJECT_NAME} PUBLIC -D__${TARGET_MCU}__)
endif ()

# Use colours
target_compile_definitions(${PROJECT_NAME} PUBLIC -DLOG_USE_COLOR)

target_include_directories(${PROJECT_NAME} PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/
        )

set_property(TARGET ${PROJECT_NAME} PROPERTY C_STANDARD 11)
