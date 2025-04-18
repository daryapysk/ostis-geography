set(SOURCES
        "DanceStudiosModule.cpp"
        "keynodes/DanceStudiosKeynodes.cpp"
        "search/DanceStudiosByPropertyInNumericalRangeFinder.cpp"
	      "agent/SearchDanceStudiosByTypeAgent.cpp"
		    "agent/SearchDanceStudiosByCityAgent.cpp"
        "agent/SearchDanceStudiosByFoundingYearAgent.cpp"
        "search/DanceStudiosByString.cpp"
        )

set(HEADERS
        "DanceStudiosModule.hpp"
        "keynodes/DanceStudiosKeynodes.hpp"
        "search/DanceStudiosByPropertyInNumericalRangeFinder.hpp"
	      "agent/SearchDanceStudiosByTypeAgent.hpp"
		    "agent/SearchDanceStudiosByCityAgent.hpp"
        "agent/SearchDanceStudiosByFoundingYearAgent.hpp"
        "search/DanceStudiosByString.hpp"
        )

set(DANCE_STUDIOS_MODULE_GENERATED_DIR ${CMAKE_CURRENT_LIST_DIR}/generated)
include_directories(${CMAKE_CURRENT_LIST_DIR} ${SC_MEMORY_SRC} ${SC_KPM_SRC} ${DANCE_STUDIOS_MODULE_GENERATED_DIR})

add_library(dance_studiosModule SHARED ${SOURCES} ${HEADERS})
target_link_libraries(dance_studiosModule sc-memory sc-agents-common)

sc_codegen_ex(dance_studiosModule ${CMAKE_CURRENT_LIST_DIR} ${CMAKE_CURRENT_LIST_DIR}/generated)

if(${SC_CLANG_FORMAT_CODE})
	target_clangformat_setup(dance_studiosModule)
endif()
