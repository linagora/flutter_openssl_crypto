cmake_minimum_required(VERSION 3.6)
project(flutter_openssl_crypto)
add_library(${PROJECT_NAME} SHARED empty.c)

# Declare prebuilt libcrypto.so
add_library(crypto SHARED IMPORTED)
set_target_properties(crypto PROPERTIES
    IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libcrypto.so
)

# Link against the prebuilt OpenSSL libraries
target_link_libraries(${PROJECT_NAME}
    crypto
    android
    log
)
