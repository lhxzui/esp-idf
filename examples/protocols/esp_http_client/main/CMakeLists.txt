# Embed the server root certificate into the final binary
#
# (If this was a component, we would set COMPONENT_EMBED_TXTFILES here.)
set(requires "")
if(${IDF_TARGET} STREQUAL "linux")
    list(APPEND requires esp_stubs esp-tls esp_http_client)
endif()
idf_component_register(SRCS "esp_http_client_example.c"
                    INCLUDE_DIRS "."
                    REQUIRES ${requires}
                    EMBED_TXTFILES howsmyssl_com_root_cert.pem
                    postman_root_cert.pem)
