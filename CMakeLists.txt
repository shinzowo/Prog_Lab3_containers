cmake_minimum_required(VERSION 3.5.0)
project(containers VERSION 0.1.0 LANGUAGES C CXX)

# Устанавливаем стандарт C++
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})

# Основной исполняемый файл
add_executable(containers main.cpp)

# Опции компилятора для поддержки концептов в GCC
target_compile_options(containers PRIVATE -fconcepts)

# Устанавливаем путь для исполняемых файлов при установке пакета
install(TARGETS containers DESTINATION bin)

# Включаем CPack для создания пакетов (DEB и ZIP)
include(CPack)

# Устанавливаем генераторы пакетов (DEB для Linux, ZIP для Windows)
set(CPACK_GENERATOR "DEB;ZIP")

# Настраиваем версию пакета
set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

# Контактные данные для пакета (можно указать свои данные)
set(CPACK_PACKAGE_CONTACT "example@example.com")