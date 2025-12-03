# ollama-0.13.1_enableAmdMi50
Modify ollama source code to enable amd instinct mi50 gpu(Depend on rocm7.0.2)

build cmd:
rm -rf build && mkdir build && cd build && cmake -Dhip_DIR=/opt/rocm-7.0.2/lib/cmake/hip -DCMAKE_PREFIX_PATH=/opt/rocm-7.0.2 -DAMDGPU_TARGETS=gfx906 -DGGML_HIP_ROCWMMA_FATTN=ON -DCMAKE_BUILD_TYPE=Release .. && cmake --build . -j$(nproc)

generate main program file:
go build -tags=nolegacy -ldflags="-s -w -X"
