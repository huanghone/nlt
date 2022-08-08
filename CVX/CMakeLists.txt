FILE(GLOB cvx_SRC *.hh *.cc *.cpp *.h *.hpp)
source_group("" FILES ${cvx_SRC})

add_executable(cvx ${cvx_SRC})