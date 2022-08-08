FILE(GLOB bfc_SRC *.hh *.cc *.cpp *.h *.hpp)
source_group("" FILES ${bfc_SRC})

add_executable(bfc ${bfc_SRC})