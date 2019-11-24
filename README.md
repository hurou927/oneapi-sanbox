# OneAPI


## LIB

```sh
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/intel/inteloneapi/compiler/2021.1-beta03/linux/compiler/lib/intel64_lin/

```


## Util

```sh
fd "so$" /opt/intel | grep -v python | xargs -I {} dirname {} | sort | uniq

```

## Get Devie Info

```cpp
#include <vector>
#include <CL/sycl.hpp>


namespace sycl = cl::sycl;

int main() {
    auto platforms = sycl::platform::get_platforms();
    for (auto &platform : platforms) {
        std::cout << "Platform: "
            << platform.get_info<sycl::info::platform::name>()
            << std::endl;
        auto devices = platform.get_devices();
        for (auto &device : devices ) {
            std::cout << " Device: "
                << device.get_info<sycl::info::device::name>()
                << std::endl;
        }
    }
}
```