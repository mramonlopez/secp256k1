cmake_minimum_required(VERSION 3.18)
set(CMAKE_CXX_STANDARD 17)

set(LIB_NAME secp256k1)
project(${LIB_NAME} VERSION 0.1 LANGUAGES CXX C)

option(ECMULT_GEN_PREC_BITS "ecmult gen prec. bits" 4)

set(SOURCE_FILES 
	src/bench.c
	src/bench_ecmult.c
	src/bench_internal.c
	src/precompute_ecmult.c
	src/precompute_ecmult_gen.c
	src/precomputed_ecmult.c
	src/precomputed_ecmult_gen.c
	src/secp256k1.c
	# src/tests.c
	# src/tests_exhaustive.c
	# src/valgrind_ctime_test.c
)

add_library(${LIB_NAME} ${SOURCE_FILES})

target_include_directories(${LIB_NAME} PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}/src
	${CMAKE_CURRENT_SOURCE_DIR}/include
)

add_compile_definitions(${LIB_NAME} PUBLIC
    ECMULT_GEN_PREC_BITS=4
	ECMULT_WINDOW_SIZE=15
)