cmake_minimum_required(VERSION 3.2)
project(PLAY)
include_directories(
        ${PLAY_SOURCE_DIR}/include
)

SET( CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE "${PLAY_SOURCE_DIR}/bin/Release")
SET( CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG "${PLAY_SOURCE_DIR}/bin/Debug")

set(play_src
	main.cpp
)

add_executable(PLAY ${play_src})
target_link_libraries(PLAY  libportaudio.a rt asound  pthread m libcrypto.a libz.a dl )

add_custom_command(TARGET PLAY
	POST_BUILD
	COMMAND ${CMAKE_COMMAND} -E copy_if_different ${CMAKE_CURRENT_SOURCE_DIR}/heming.pcm  ${PLAY_SOURCE_DIR}/build/heming.pcm
	)