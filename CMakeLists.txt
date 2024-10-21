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

set(CPACK_GENERATOR "DEB")  # Добавьте ZIP, если хотите его тоже
set(CPACK_PACKAGE_NAME "containers")
set(CPACK_PACKAGE_VERSION "0.1.0")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Your Name")  # Укажите ваше имя
set(CPACK_DEBIAN_PACKAGE_DESCRIPTION "My container package")
set(CPACK_PACKAGE_CONTACT example@example.com)
