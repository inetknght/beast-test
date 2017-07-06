To reproduce an issue observed,

git clone https://github.com/inetknght/beast-test &&
cd beast-test &&
git submodule update --init --recursive &&
mkdir build &&
cd build &&
cmake ../ -DBeast_BUILD_EXAMPLES=OFF -DBeast_BUILD_TESTS=OFF && make -j$(nproc) ../ && make -j$(nproc)

# Observe error: 
#
#[ 50%] Building CXX object src/CMakeFiles/beast_test.dir/main.cpp.o
#In file included from beast-test/src/http_async_port.hpp:13:0,
#                 from beast-test/src/main.cpp:10:
#beast-test/src/http_base.hpp:11:33: fatal error: beast/core/string.hpp: No such file or directory
# #include <beast/core/string.hpp>
#                                 ^
#compilation terminated.
#
# Make change

cd ../beast &&
git remote add inetknght https://github.com/inetknght/Beast &&
git fetch inetknght &&
git checkout inetknght/fix-include-directories &&
cd ../build &&
make -j$(nproc)

# Observe success!
