# Coremark 构建入口（框架侧 glue，上游仓库保持原样）。
#
# 与 modules/coremark/coremark.clayer.yml 一致：5 个源文件，include 路径
# 为模块根与 ./simple（core_portme.h 由工程提供）。

add_library(omni_module_coremark OBJECT
    "${OMNI_MODULE_COREMARK_SRC}/core_list_join.c"
    "${OMNI_MODULE_COREMARK_SRC}/core_main.c"
    "${OMNI_MODULE_COREMARK_SRC}/core_matrix.c"
    "${OMNI_MODULE_COREMARK_SRC}/core_state.c"
    "${OMNI_MODULE_COREMARK_SRC}/core_util.c")

target_include_directories(omni_module_coremark PUBLIC
    "${OMNI_MODULE_COREMARK_SRC}"
    "${OMNI_MODULE_COREMARK_SRC}/simple")
target_link_libraries(omni_module_coremark PUBLIC
    omni::framework omni::config omni::hal)

omni_apply_arch(omni_module_coremark)
omni_apply_warnings(omni_module_coremark)
