cmake_minimum_required(VERSION 2.8)

project(litehtml)

if (NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
    message(STATUS "No build type selected, default to Release")
    set(CMAKE_BUILD_TYPE "Release")
endif()

if(NOT MSVC)
	set(CMAKE_CXX_FLAGS "-std=c++11")
	set(CMAKE_CXX_FLAGS_DEBUG "-O0 -DDEBUG -g")
	set(CMAKE_C_FLAGS_DEBUG "-std=c99 -O0 -DDEBUG -g")
	set(CMAKE_CXX_FLAGS_RELEASE "-O3")
	set(CMAKE_C_FLAGS_RELEASE "-std=c99 -O3")
endif()

add_definitions(-DLITEHTML_UTF8)

set(SOURCE_LITEHTML     src/background.cpp
                        src/box.cpp
                        src/context.cpp
                        src/css_length.cpp
                        src/css_selector.cpp
                        src/document.cpp
                        src/el_anchor.cpp
                        src/el_base.cpp
                        src/el_before_after.cpp
                        src/el_body.cpp
                        src/el_break.cpp
                        src/el_cdata.cpp
                        src/el_comment.cpp
                        src/el_div.cpp
                        src/element.cpp
                        src/el_font.cpp
                        src/el_image.cpp
                        src/el_link.cpp
                        src/el_para.cpp
                        src/el_script.cpp
                        src/el_space.cpp
                        src/el_style.cpp
                        src/el_table.cpp
                        src/el_td.cpp
                        src/el_text.cpp
                        src/el_title.cpp
                        src/el_tr.cpp
                        src/html.cpp
                        src/html_tag.cpp
                        src/iterators.cpp
                        src/media_query.cpp
                        src/style.cpp
                        src/stylesheet.cpp
                        src/table.cpp
                        src/utf8_strings.cpp
                        src/web_color.cpp
)

set(SOURCE_GUMBO        src/gumbo/attribute.c
                        src/gumbo/char_ref.c
                        src/gumbo/error.c
                        src/gumbo/parser.c
                        src/gumbo/string_buffer.c
                        src/gumbo/string_piece.c
                        src/gumbo/tag.c
                        src/gumbo/tokenizer.c
                        src/gumbo/utf8.c
                        src/gumbo/util.c
                        src/gumbo/vector.c
)

set(HEADERS_LITEHTML    include/litehtml.h
                        src/el_space.h
                        src/el_text.h
                        src/el_before_after.h
                        src/html_tag.h
                        src/el_tr.h
                        src/el_title.h
                        src/el_td.h
                        src/el_table.h
                        src/el_style.h
                        src/el_script.h
                        src/el_para.h
                        src/el_link.h
                        src/el_image.h
                        src/el_font.h
                        src/el_div.h
                        src/el_comment.h
                        src/el_cdata.h
                        src/el_break.h
                        src/el_body.h
                        src/el_base.h
                        src/el_anchor.h
                        src/element.h
                        src/html.h
                        src/document.h
                        src/stylesheet.h
                        src/media_query.h
                        src/utf8_strings.h
                        src/web_color.h
                        src/table.h
                        src/types.h
                        src/style.h
                        src/os_types.h
                        src/iterators.h
                        src/css_position.h
                        src/css_selector.h
                        src/css_margins.h
                        src/css_offsets.h
                        src/css_length.h
                        src/box.h
                        src/context.h
                        src/borders.h
                        src/attributes.h
                        src/background.h
)

set(HEADERS_GUMBO       src/gumbo/gumbo.h
                        src/gumbo/attribute.h
                        src/gumbo/char_ref.h
                        src/gumbo/error.h
                        src/gumbo/insertion_mode.h
                        src/gumbo/parser.h
                        src/gumbo/string_buffer.h
                        src/gumbo/string_piece.h
                        src/gumbo/tag_enum.h
                        src/gumbo/tag_gperf.h
                        src/gumbo/tag_sizes.h
                        src/gumbo/tag_strings.h
                        src/gumbo/token_type.h
                        src/gumbo/tokenizer.h
                        src/gumbo/tokenizer_states.h
                        src/gumbo/utf8.h
                        src/gumbo/util.h
                        src/gumbo/vector.h
)

add_library(litehtml STATIC ${SOURCE_LITEHTML} ${SOURCE_GUMBO} ${HEADERS_LITEHTML} ${HEADERS_GUMBO})

if(WIN32)
     target_include_directories(litehtml PUBLIC src/gumbo)
endif()

