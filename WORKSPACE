load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# import project repositories 
YGG_BUILD_RULES_TAG = "0.0.4"
YGG_BUILD_RULES_SHA = "96ff13d77528cacf716275caad7b7f22752e64128330e76ac24967c5e255ab58"
http_archive(
    name = "ygg_build_rules",
    strip_prefix = "Yggdrasil-%s" % YGG_BUILD_RULES_TAG,
    url = "https://github.com/mellemahp/Yggdrasil/archive/%s.zip" % YGG_BUILD_RULES_TAG
)
load("@ygg_build_rules//build_rules:ygg_multirepo_git.bzl", "ygg_git_deps")
load(":ygg.bzl", "PACKAGE_OVERRIDES")

ygg_git_deps(
    package_overrides=PACKAGE_OVERRIDES,
    repos =[
        {"name": "lambda_tools",
        "repo_name": "LambdaTools",
        "remote": "https://github.com/mellemahp/LambdaTools"}
    ],
    default_branch="main"
)

# import libraries from maven
RULES_JVM_EXTERNAL_TAG = "2.8"
RULES_JVM_EXTERNAL_SHA = "79c9850690d7614ecdb72d68394f994fef7534b292c4867ce5e7dec0aa7bdfad"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)
load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        # avro code gen
        "org.apache.avro:avro-tools:1.10.2"        
    ],
    repositories = [
        "https://repo1.maven.org/maven2",
    ],
)