filegroup(
    name = "rune_page_event_avro", 
    srcs = ["events/runePageEvent.avsc"],
    visibility = ["//visibility:public"]
)

genrule(
    name = "rune_page_event_java",
    srcs = ["@maven//:org_apache_avro_avro_tools", "rune_page_event_avro"],
    cmd = """
     java -jar $(location @maven//:org_apache_avro_avro_tools) compile schema $(location rune_page_event_avro) .
     cp -R com/hmellema/runepageApi/runePageEvent.java $(@D)
    """,
    outs = ["runePageEvent.java"],
    message = "Generating Java Objects from avro schema",
    visibility = ["//visibility:public"]
)

java_library(
    name = "rune_page_event_java_lib",
    srcs = ["rune_page_event_java"],
    deps = ["@maven//:org_apache_avro_avro_tools"]
)