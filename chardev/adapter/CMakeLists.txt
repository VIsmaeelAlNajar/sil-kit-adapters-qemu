add_library(
    ChardevSocketToPubSubAdapter STATIC
    ChardevSocketToPubSubAdapter.cpp)
    
target_include_directories(ChardevSocketToPubSubAdapter 
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} 
           ${CMAKE_SOURCE_DIR})
target_link_libraries(ChardevSocketToPubSubAdapter
    PRIVATE
        asio
        SilKit::SilKit
)
set_target_properties(ChardevSocketToPubSubAdapter 
	PROPERTIES
	#ensure SilKit shared libraries can be loaded
    INSTALL_RPATH "$ORIGIN"
    BUILD_RPATH "$ORIGIN"
    RUNTIME_OUTPUT_DIRECTORY $<$<BOOL:ALWAYS>:${SILKIT_ADAPTERS_QEMU_OUTPUT_DIRECTORY}>
)
