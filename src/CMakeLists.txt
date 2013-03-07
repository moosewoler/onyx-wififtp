ENABLE_QT()

file(GLOB HDRS *.h)
file(GLOB SRCS *.cpp *.c)
set (SRCS ${HDRS} ${SRCS})

# TODO: put QT Moc files here.
set (MOC_HDRS ds_application.h ds_view.h vsftpd.h)
QT4_WRAP_CPP(MOC_SRCS ${MOC_HDRS})

# TODO: put resources here.
set (RESOURCE_SRCS res.qrc)
QT4_ADD_RESOURCES(IMAGES_RES ${RESOURCE_SRCS})

add_executable(${OUTPUT_NAME}.oar ${SRCS} ${MOC_SRCS} ${IMAGES_RES})
target_link_libraries(${OUTPUT_NAME}.oar
   onyx_data
   onyx_screen
   onyx_wireless
   onyx_sys
   onyx_ui
   ${QT_LIBRARIES}
   ${ADD_LIB}
)
