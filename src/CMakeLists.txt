
file (GLOB_RECURSE
    TOMCRYPT_SOURCES
    ${PROJECT_SOURCE_DIR}/src/*)
# include_directories()
add_library (tomcrypt ${TOMCRYPT_SOURCES})

target_include_directories (tomcrypt PUBLIC ${CMAKE_SOURCE_DIR}/src/headers)

# ja : add include paths
# resolve ISO C99 requires whitespace after the macro name
# src/headers
# set_target_properties (libtomcrypt PROPERTIES
#    IMPORTED_LOCATION "")

# From the default make
# -Wall -Wsign-compare -Wshadow -DLTC_SOURCE 
# -Wextra -Wsystem-headers -Wbad-function-cast 
# -Wcast-align -Wstrict-prototypes -Wpointer-arith 
# -Wdeclaration-after-statement -Wwrite-strings -Wno-type-limits -O3 
# -funroll-loops -fomit-frame-pointer -DGIT_VERSION="git-v1.18.2-dirty

# add_compile_definitions (LTC_SOURCE)
set (TOMCRYPT_GIT_VERSION "git-v1.18.2-dirty")

target_compile_definitions (tomcrypt 
    PUBLIC
        # Wall
        # Wsign-compare
        # Wshadow
        "LTC_SOURCE"
        "GIT_VERSION=${TOMCRYPT_GIT_VERSION}"
)

# aes
# -DENCRYPT_ONLY
# -DUSE_LTM -DLTM_DESC
