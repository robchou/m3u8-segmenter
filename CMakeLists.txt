cmake_minimum_required(VERSION 2.8)
project(segmenter)

find_package(PkgConfig REQUIRED)
pkg_check_modules(FFMPEG REQUIRED libavcodec libavformat libavutil libswscale libswresample)

set(m3u8_segmenter_source_files
    m3u8-segmenter.c
    )

include_directories(${FFMPEG_INCLUDE_DIRS})
link_directories(
    ${FFMPEG_LIBRARY_DIRS}
    )

add_executable(m3u8-segmenter
    ${m3u8_segmenter_source_files}
    )
target_link_libraries(m3u8-segmenter
    ${FFMPEG_LIBRARIES}
)
