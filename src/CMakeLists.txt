FILE(GLOB nlt_SRC *.hh *.cc *.cpp *.h *.hpp)
source_group("" FILES ${nlt_SRC})

add_executable(eval_rbot ${nlt_SRC})
target_link_libraries(eval_rbot ${LINK_LIBS})
