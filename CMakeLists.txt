cmake_minimum_required(VERSION 3.5.0)
project(containers VERSION 0.1.0 LANGUAGES C CXX)

# Устанавливаем стандарт C++
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Основной исполняемый файл
add_executable(containers main.cpp)

# Опции компилятора для поддержки концептов в GCC
target_compile_options(containers PRIVATE -fconcepts)

# Устанавливаем путь для исполняемых файлов при установке пакета
install(TARGETS containers DESTINATION bin)

# Включаем CPack для создания пакетов (DEB и ZIP)
include(CPack)

set(CPACK_GENERATOR "DEB;ZIP")
set(CPACK_PACKAGE_NAME "containers")
set(CPACK_PACKAGE_VERSION "0.1.0")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "My container package")
set(CPACK_PACKAGE_VENDOR "My Company")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Your Name")  # Важно для DEB
set(CPACK_PACKAGE_FILE_NAME "${CPACK_PACKAGE_NAME}-${CPACK_PACKAGE_VERSION}-${CMAKE_SYSTEM_NAME}")
set(CPACK_DEBIAN_PACKAGE_DEPENDS "libc6 (>= 2.27)")
set(CPACK_SOURCE_GENERATOR "TGZ;ZIP")

