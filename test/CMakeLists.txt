#[[
Copyright (C) 2020 Gordon Brown

Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
]]

function(add_cpp_test source)
  add_executable("${source}" "${source}.cpp")
  target_include_directories("${source}" PRIVATE
    ${PROJECT_SOURCE_DIR}/include)
  target_link_libraries("${source}" PRIVATE Threads::Threads)
  target_link_libraries("${source}" PUBLIC Catch2::Catch2)
  set_target_properties("${source}" PROPERTIES CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON)
  
add_test(${source} ${source})
endfunction()

enable_testing()

add_cpp_test(inline_executor)