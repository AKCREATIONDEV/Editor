cmake_minimum_required(VERSION 3.22.1)

project("oniguruma-binding")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-fvisibility=hidden")

# --- Yahan Change Kiya Hai ---
# oniguruma folder ki jagah hum seedha internet se download kar rahe hain
include(FetchContent)

FetchContent_Declare(
  oniguruma
  GIT_REPOSITORY https://github.com/kkos/oniguruma.git
  GIT_TAG        v6.9.10
)

FetchContent_MakeAvailable(oniguruma)
# -----------------------------

add_library("oniguruma-binding" SHARED binding.cpp)

target_link_libraries("oniguruma-binding" PUBLIC onig)
