# Documentation :: pmd by org.apache.easyant.plugins

# Description

# Example

```xml
<ea:plugin organisation="org.apache.easyant.plugins" module="pmd" revision="0.1"/>
```
Organisation attribute is optional. If not specified default one will be used.

```xml
<ea:plugin module="pmd" revision="0.1"/>
```

## Available targets

|target name|description|extension point|depends|
|-----------|-----------|---------------|-------|
|pmd:init||||
|pmd:cpd|generates a report for PMD's Copy/Paste Detector (CPD) tool||pmd:init|
|pmd:pmd|creates a PMD report based on the rulesets and configuration set in the plugin||pmd:init|

## Module parameters

### Properties

|property|description|required|default value|
|--------|-----------|--------|-------------|
|pmd.failonruleviolation|Whether or not to fail the build if PMD finds any problems|false|true|
|pmd.minimum.priority|The rule priority threshold; rules with lower priority than they will not be used|false|5|
|pmd.minimum.token.count|A positive integer indicating the minimum duplicate size.|false|100|
|pmd.failonerror|Whether or not to fail the build if any errors occur while processing the files|false|true|
|pmd.main.sources.includes|Pattern describing files included in pmd checks|false|**/*.java|
|pmd.ignore.literals|if true, CPD ignores literal value differences when evaluating a duplicate block. This means that foo=42; and foo=43; will be seen as equivalent. You may want to run PMD with this option off to start with and then switch it on to see what it turns up; defaults to false.|false|false|
|pmd.rulesetfiles|A comma delimited list of ruleset files ('rulesets/basic.xml,rulesets/design.xml'). If you write your own ruleset files, you can put them on the classpath and plug them in here.|false|rulesets/java/imports.xml,java-unusedcode|
|pmd.report.outputfile||false|${target.reports}/pmd.xml|
|pmd.encoding|The character set encoding (e.g. UTF-8) to use when reading the source code files|false|UTF-8|
|pmd.ignore.annotations|Ignore annotations. More and more modern frameworks use annotations on classes and methods, which can be very redundant and trigger CPD matches. With J2EE (CDI, Transaction Handling, etc) and Spring (everything) annotations become very redundant. Often classes or methods have the same 5-6 lines of annotations. This causes false positives.|false|false|
|pmd.cpd.report.outputfile|The destination file for the report. If not specified the console will be used instead.|false|${target.reports}/cpd.${pmd.format}|
|pmd.main.sources.excludes|Pattern describing files included in pmd checks|false||
|pmd.language|Flag to select the appropriate language (e.g. cpp, cs, java, php, ruby, and ecmascript); defaults to java.|false|java|
|target.reports|base directory for reports|false|${target}/reports|
|pmd.max.rule.violations|Whether or not to fail the build if PMD finds more than the value of this attribute. Note that setting this attribute does not require to set the failOnRuleViolation to true.|false|0|
|pmd.format|The format of the report (e.g. csv, text, xml); defaults to text.|false|text|
|pmd.main.sources|directory where pmd rules will be checked|false|${basedir}/src/main/java|
|pmd.ignore.identifiers|Similar to ignoreLiterals but for identifiers; i.e., variable names, methods names, and so forth; defaults to false.|false|false|

## Ivy Configurations

|name|description|extends|visibility|deprecated|
|----|-----------|-------|----------|----------|
|default|runtime dependencies artifact can be used with this conf|[]|public||
|test|this scope indicates that the dependency is not required for normal use of the application, and is only available for the test compilation and execution phases.|[]|private||
|provided|this is much like compile, but indicates you expect the JDK or a container to provide it. It is only available on the compilation classpath, and is not transitive.|[]|public||

## Dependencies Overview

|Organisation|Module|Revision|
|------------|------|--------|
|net.sourceforge.pmd|pmd|5.0.4|

