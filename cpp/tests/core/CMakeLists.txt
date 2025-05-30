target_sources(tests PRIVATE
    Blob.cpp
    CoreTest.cpp
    CUDAUtils.cpp
    Device.cpp
    EigenConverter.cpp
    HashMap.cpp
    Indexer.cpp
    Linalg.cpp
    MemoryManager.cpp
    NanoFlannIndex.cpp
    NearestNeighborSearch.cpp
    ParallelFor.cpp
    Scalar.cpp
    ShapeUtil.cpp
    SizeVector.cpp
    Tensor.cpp
    TensorCheck.cpp
    TensorFunction.cpp
    TensorList.cpp
    TensorObject.cpp
    SYCLUtils.cpp
)

if (BUILD_CUDA_MODULE)
    target_sources(tests PRIVATE
        FixedRadiusIndex.cpp
        KnnIndex.cpp
        ParallelFor.cu
    )
endif()

if (BUILD_ISPC_MODULE)
    target_sources(tests PRIVATE
        Indexer.ispc
        ParallelFor.ispc
    )
endif()

# TODO: cmake does not currently build this test!
# if (BUILD_SYCL_MODULE)
#     target_sources(tests PRIVATE
#         ParallelForSYCL.cpp
#     )
#     set_source_files_properties(ParallelForSYCL.cpp PROPERTIES
#         COMPILE_OPTIONS "-fsycl;-fsycl-targets=spir64_gen")
# endif()