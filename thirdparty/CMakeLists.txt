# tinyply
include_directories(tinyply/source)
add_library(tinyply SHARED tinyply/source/tinyply.cpp tinyply/source/tinyply.h)

# Spectra
include_directories(spectra/include)

# pmc
include_directories(pmc/include)
set(PMC_SOURCE_FILES
    pmc/pmc_heu.cpp
    pmc/pmc_maxclique.cpp
    pmc/pmcx_maxclique.cpp
    pmc/pmcx_maxclique_basic.cpp
    pmc/pmc_cores.cpp
    pmc/pmc_utils.cpp
    pmc/pmc_graph.cpp
    pmc/pmc_clique_utils.cpp
)

add_library(pmc SHARED ${PMC_SOURCE_FILES})

