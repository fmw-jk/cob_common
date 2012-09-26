project(cob_description)

catkin_project(${PROJECT_NAME}
  	INCLUDE_DIRS include
)

find_package(rosconsole REQUIRED)
include_directories(${rosconsole_INCLUDE_DIRS})

add_executable(test_urdf test/test_urdf.cpp)
target_link_libraries(test_urdf ${rosconsole_LIBRARIES}
	${GTEST_LIBRARIES}
)

#install(TARGETS test_urdf
#	DESTINATION bin
#)

# install all manifests; for compatibility with old build system
install(FILES manifest-to-install.xml
        DESTINATION share/cob_srvs RENAME manifest.xml)





#rosbuild_add_gtest_build_flags(test_urdf)

# mesh file generations
#rosbuild_find_ros_package(ivcon)
#rosbuild_find_ros_package(convex_decomposition)

# iterate through all the stl files to:
#  1. convert to *.iv files
#  2. generate convex decomposed .stl
#file(GLOB cob_stl_files ${CMAKE_CURRENT_SOURCE_DIR}/meshes/*/*.stl)
#set(cob_gen_files "")
#
#foreach(it ${cob_stl_files})
#  get_filename_component(basepath ${it} PATH)
#  get_filename_component(basename ${it} NAME_WE)
#
#  IF ( ${basename} MATCHES "_convex" )
#
#    message("ignoring stale .._convex.stl file:",${basename})
#
#  ELSE ( ${basename} MATCHES "_convex" )
#
#    # create subdirectory convex
#    add_custom_command(
#      OUTPUT ${basepath}/convex
#      # CMake 2.4 doesn't offer the make_directory command.
#      #COMMAND ${CMAKE_COMMAND} -E make_directory
#      COMMAND mkdir -p
#      ARGS ${basepath}/convex)
#
#    # create subdirectory iv
#    add_custom_command(
#      OUTPUT ${basepath}/iv
#      # CMake 2.4 doesn't offer the make_directory command.
#      #COMMAND ${CMAKE_COMMAND} -E make_directory
#      COMMAND mkdir -p
#      ARGS ${basepath}/iv)
#
#    #create obj files for convex decomposition from stl files
#    add_custom_command(
#      OUTPUT ${basepath}/convex/${basename}.obj
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${it} ${basepath}/convex/${basename}.obj
#      DEPENDS ${it} ${basepath}/convex)
#
#    set(cob_gen_files ${cob_gen_files} ${basepath}/convex/${basename}.obj)
#
#    #convex decompose object files
#    add_custom_command(
#      OUTPUT ${basepath}/convex/${basename}_convex.obj
#      COMMAND ${convex_decomposition_PACKAGE_PATH}/convex_decomposition/bin/convex_decomposition
#      ARGS ${basepath}/convex/${basename}.obj -v12 -p10
#      DEPENDS ${basepath}/convex/${basename}.obj ${basepath}/convex)
#
#    set(cob_gen_files ${cob_gen_files} ${basepath}/convex/${basename}_convex.obj)
#
#    #convert obj files back to stlb, put in directory named convex
#    add_custom_command(
#      OUTPUT ${basepath}/convex/${basename}_convex.stlb
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${basepath}/convex/${basename}_convex.obj ${basepath}/convex/${basename}_convex.stlb
#      DEPENDS ${it} ${basepath}/convex ${basepath}/convex/${basename}_convex.obj)
#
#    set(cob_gen_files ${cob_gen_files} ${basepath}/convex/${basename}_convex.stlb)
#
#    #convert obj files back to stla, put in directory named convex
#    add_custom_command(
#      OUTPUT ${basepath}/convex/${basename}_convex.stla
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${basepath}/convex/${basename}_convex.obj ${basepath}/convex/${basename}_convex.stla
#      DEPENDS ${it} ${basepath}/convex ${basepath}/convex/${basename}_convex.obj)
#
#    set(cob_gen_files ${cob_gen_files} ${basepath}/convex/${basename}_convex.stla)
#
#    #convert stl files to stlb, put in directory named stlb
#    add_custom_command(
#      OUTPUT ${basepath}/${basename}.stlb
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${basepath}/${basename}.stl ${basepath}/${basename}.stlb
#      DEPENDS ${it} ${basepath}/${basename}.stl)
#
#    set(cob_gen_files ${cob_gen_files} ${basepath}/${basename}.stlb)
#
#    #create iv files
#    add_custom_command(
#      OUTPUT ${basepath}/iv/${basename}.iv
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${it} ${basepath}/iv/${basename}.iv
#      DEPENDS ${basepath}/iv ${it})
#    add_custom_command(
#      OUTPUT ${basepath}/convex/${basename}_convex.iv
#      COMMAND ${ivcon_PACKAGE_PATH}/bin/ivcon
#      ARGS ${basepath}/convex/${basename}_convex.obj ${basepath}/convex/${basename}_convex.iv
#      DEPENDS ${it} ${basepath}/convex ${basepath}/convex/${basename}_convex.obj)
#     
#    set(cob_gen_files ${cob_gen_files} ${basepath}/iv/${basename}.iv ${basepath}/convex/${basename}_convex.iv)
#
#  ENDIF ( ${basename} MATCHES "_convex" )
#
#endforeach(it)
#
#add_custom_target(media_files ALL DEPENDS ${cob_gen_files})

