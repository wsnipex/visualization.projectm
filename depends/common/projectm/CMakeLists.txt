project(projectm)

cmake_minimum_required(VERSION 2.8)

include(ExternalProject)
externalproject_add(projectm
                    SOURCE_DIR ${CMAKE_SOURCE_DIR}
                    CONFIGURE_COMMAND cd <SOURCE_DIR> && autoreconf -vif && CXXFLAGS=-I${OUTPUT_DIR}/include CFLAGS=-I${OUTPUT_DIR}/include LDFLAGS=-L${OUTPUT_DIR}/lib ./configure --disable-shared --prefix=${OUTPUT_DIR} --with-pic
                    BUILD_COMMAND make
                    INSTALL_COMMAND ""
                    BUILD_IN_SOURCE 1)

install(CODE "execute_process(COMMAND make install WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
