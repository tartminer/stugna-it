cmake_minimum_required(VERSION 3.5)

project(stugna-it LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)



include(FindPkgConfig)


set(src
   main.cpp
   utils.cpp
   httpserver.cpp
   proxy.cpp
   gun.cpp
   jobs.cpp
   job.cpp
   uaheaders.cpp
   stats.cpp
   multigun.cpp
)

set(THREADS_PREFER_PTHREAD_FLAG ON)
set(CURL_STATICLIB OFF)


find_package(Threads REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(CURL REQUIRED)

add_executable(stugna-it ${src})
target_link_libraries(stugna-it PUBLIC ${CURL_LIBRARIES} Threads::Threads OpenSSL::SSL CURL::libcurl)

