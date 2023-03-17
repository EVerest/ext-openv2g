# OpenV2G library

add_library(openv2g SHARED)
add_library(everest::openv2g ALIAS openv2g)

set_target_properties(openv2g PROPERTIES SOVERSION ${SOVERSION})

target_sources(openv2g
    PRIVATE
        appHandshake/appHandEXIDatatypes.c
        appHandshake/appHandEXIDatatypesDecoder.c
        appHandshake/appHandEXIDatatypesEncoder.c
        codec/BitInputStream.c
        codec/BitOutputStream.c
        codec/ByteStream.c
        codec/DecoderChannel.c
        codec/EncoderChannel.c
        codec/EXIHeaderDecoder.c
        codec/EXIHeaderEncoder.c
        codec/MethodsBag.c
        din/dinEXIDatatypes.c
        din/dinEXIDatatypesDecoder.c
        din/dinEXIDatatypesEncoder.c
        iso1/iso1EXIDatatypes.c
        iso1/iso1EXIDatatypesDecoder.c
        iso1/iso1EXIDatatypesEncoder.c
        iso2/iso2EXIDatatypes.c
        iso2/iso2EXIDatatypesDecoder.c
        iso2/iso2EXIDatatypesEncoder.c
        transport/v2gtp.c
        xmldsig/xmldsigEXIDatatypes.c
        xmldsig/xmldsigEXIDatatypesDecoder.c
        xmldsig/xmldsigEXIDatatypesEncoder.c
)

target_include_directories(openv2g
    PUBLIC
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

target_compile_features(openv2g PUBLIC c_std_99)
