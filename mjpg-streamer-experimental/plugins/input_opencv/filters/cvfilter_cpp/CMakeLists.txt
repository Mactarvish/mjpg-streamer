
MJPG_STREAMER_PLUGIN_OPTION(cvfilter_cpp "OpenCV example filter")
MJPG_STREAMER_PLUGIN_COMPILE(cvfilter_cpp filter_cpp.cpp)
target_link_libraries(cvfilter_cpp ${OpenCV_LIBS})
