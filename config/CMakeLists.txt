set(breezedecoration_config_SRCS
    ../breezeexceptionlist.cpp
    breezeconfigwidget.cpp
    breezedetectwidget.cpp
    breezeexceptiondialog.cpp
    breezeexceptionlistwidget.cpp
    breezeexceptionmodel.cpp
    breezeitemmodel.cpp)
ki18n_wrap_ui(breezedecoration_config_SRCS ui/breezeconfigurationui.ui
              ui/breezeexceptiondialog.ui ui/breezeexceptionlistwidget.ui)

kcoreaddons_add_plugin(
  kcm_breezeenhanceddecoration SOURCES kcm_breezeenhanceddecoration
  ${breezedecoration_config_SRCS} INSTALL_NAMESPACE
  "${KDECORATION_KCM_PLUGIN_DIR}")
kconfig_add_kcfg_files(kcm_breezeenhanceddecoration ../breezesettings.kcfgc)
target_include_directories(kcm_breezeenhanceddecoration
                           PRIVATE ${CMAKE_SOURCE_DIR} ${CMAKE_BINARY_DIR}/)
target_link_libraries(
  kcm_breezeenhanceddecoration
  PUBLIC Qt6::Core Qt6::Gui Qt6::DBus Qt6::Core5Compat
  PRIVATE KF6::ConfigCore KF6::CoreAddons KF6::GuiAddons KF6::I18n
          KF6::KCMUtils)
kcmutils_generate_desktop_file(kcm_breezeenhanceddecoration)
