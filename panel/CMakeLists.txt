
add_library(panel STATIC
            p_above.c
            panel.c
            p_below.c
            p_bottom.c
            p_delete.c
            p_hidden.c
            p_hide.c
            p_move.c
            p_new.c
            p_replace.c
            p_show.c
            p_top.c
            p_update.c
            p_user.c
            p_win.c)

target_compile_definitions(panel PRIVATE "_DEFAULT_SOURCE"
                                         "_XOPEN_SOURCE=600"
                                         "HAVE_CONFIG_H"
                                         "DATA_DIR=\"/usr/share\"")
target_include_directories(panel PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}"
                                         "${CMAKE_CURRENT_SOURCE_DIR}/../include"
                                         "${CMAKE_CURRENT_SOURCE_DIR}/../ncurses")
target_include_directories(panel PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/../gen/include")

target_link_libraries(panel PUBLIC ncurses)

install(TARGETS panel DESTINATION "lib")
