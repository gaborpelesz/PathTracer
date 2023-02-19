add_executable( PathTracer WIN32
                ${CMAKE_CURRENT_LIST_DIR}/main.cpp
                ${CMAKE_CURRENT_LIST_DIR}/RayTracer.cpp
)

target_link_libraries( PathTracer PRIVATE
    dxgi.lib d3d12.lib d3dcompiler.lib
)
