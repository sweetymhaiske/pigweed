#
#    Copyright (c) 2021 Project CHIP Authors
#    All rights reserved.
#
#    Licensed under the Apache License, Version 2.0 (the "License");
#    you may not use this file except in compliance with the License.
#    You may obtain a copy of the License at
#
#        http://www.apache.org/licenses/LICENSE-2.0
#
#    Unless required by applicable law or agreed to in writing, software
#    distributed under the License is distributed on an "AS IS" BASIS,
#    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#    See the License for the specific language governing permissions and
#    limitations under the License.

# The list of src and include dirs must be in sync with that in pigweed-app/esp32/main/component.mk
idf_component_register(PRIV_INCLUDE_DIRS 
                     "${CMAKE_CURRENT_LIST_DIR}"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/src"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/src/lib"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_log"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_sys_io/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_assert/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_assert_log/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_assert_log/public_overrides" 
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_bytes/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_checksum/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_chrono"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_containers/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_hdlc/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_log/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_log_basic/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_log_basic/public_overrides"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_span/public_overrides"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_span/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_polyfill/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_polyfill/standard_library_public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_polyfill/public_overrides"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_rpc/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_rpc/nanopb/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_rpc/raw/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_protobuf/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_status/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_stream/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_result/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_varint/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_preprocessor/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/pigweed/repo/pw_rpc/system_server/public"
                     "${CMAKE_SOURCE_DIR}/third_party/connectedhomeip/third_party/nanopb/repo"
                     "${CMAKE_SOURCE_DIR}/../../platform/esp32/pw_sys_io/public"
                     "${CMAKE_SOURCE_DIR}/../../common/pigweed"
                     "${CMAKE_SOURCE_DIR}/../../../src/lib/support"
                     "${CMAKE_SOURCE_DIR}/build/config"
                    
                      SRC_DIRS
                     "${CMAKE_CURRENT_LIST_DIR}"
                     "${CMAKE_SOURCE_DIR}/../../common/pigweed"
                      PRIV_REQUIRES bt chip)

idf_component_get_property(chip_lib chip COMPONENT_LIB)
target_include_directories(${chip_lib} PRIVATE $<TARGET_PROPERTY:${COMPONENT_LIB},INCLUDE_DIRECTORIES>)

set_property(TARGET ${COMPONENT_LIB} PROPERTY CXX_STANDARD 14) 
target_compile_options(${COMPONENT_LIB} PRIVATE "-DLWIP_IPV6_SCOPES=0" "-DCHIP_HAVE_CONFIG_H")
