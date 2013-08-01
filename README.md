**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Maven License Plugin](#maven-license-plugin)
	- [Maven Repository](#maven-repository)
	- [Documentation](#documentation)
		- [Detailed Maven documentation](#detailed-maven-documentation)
		- [Goals](#goals)
		- [Configuration](#configuration)
	- [Supported comment types](#supported-comment-types)
- [summary Give an example of an additional header definition for .Net regions.](#summary-give-an-example-of-an-additional-header-definition-for-net-regions)
- [region License](#region-license)
- [endregion](#endregion)
- [summary How to use license-maven-plugin](#summary-how-to-use-license-maven-plugin)
- [](#)
- [](#-1)
- [](#-2)
- [](#-3)

# Maven License Plugin #

Basically, when you are developing a project either in open source or in a company, you often need to add at the top of your source files a license to protect your work. I didn't find any maven plugin on Internet to help you maintain these license headers. By maintaining, i mean checking if the header is here or not, generating a report and of course having the possibility to update / reformat missing license headers.

__Features:__

  * `check`: check if header is missing in some source file
  * `format`: add headers if missing
  * `remove`: can remove existing header
  * `update`: update existing header with a new one
  * `custom mappings`: enables easy support of new file extensions
  * `variable replacement`: You can add some variable in your header, such as ${year}, ${owner} and they will be replaced by the corresponding values taken from the pom or system properties.

__Project:__

 - __Build Status:__ [![Build Status](https://travis-ci.org/mycila/license-maven-plugin.png?branch=master)](https://travis-ci.org/mycila/license-maven-plugin)
 - __Issues:__ https://github.com/mycila/license-maven-plugin/issues

## Maven Repository ##

 __Releases__ 

Available in Maven Central Repository: http://repo1.maven.org/maven2/com/mycila/license-maven-plugin/

 __Snapshots__
 
Available in OSS Repository:  https://oss.sonatype.org/content/repositories/snapshots/com/mycila/license-maven-plugin/

__Plugin declaration__

    <plugin>
        <groupId>com.mycila</groupId>
        <artifactId>license-maven-plugin</artifactId>
        <version>X.Y.ga</version>
        <configuration>
            <header>com/mycila/licenses/APACHE-2</header>
            <properties>
                <owner>Mycila</owner>
                <year>${project.inceptionYear}</year>
                <email>mathieu.carbou@gmail.com</email>
            </properties>
            <excludes>
                <exclude>**/README</exclude>
                <exclude>src/test/resources/**</exclude>
                <exclude>src/main/resources/**</exclude>
            </excludes>
        </configuration>
        <dependencies>
            <dependency>
                <groupId>com.mycila</groupId>
                <artifactId>licenses</artifactId>
                <version>1</version>
            </dependency>
        </dependencies>
    </plugin>

## Documentation ##

### Detailed Maven documentation ###

The detailed Maven Plugin Documentation generated for each build is available here:

 - [2.0.rc1](http://mycila.github.io/license-maven-plugin/reports/2.0.rc1/index.html)

### Goals ###

  * `license:check`: verify if some files miss license header
  * `license:format`: add the license header when missing. If a header is existing, it is updated to the new one.
  * `license:remove`: remove existing license header

### Configuration ###

The table below shows all the available options you can use in the configure section of the plugin. A lot of are also available from the command-line. To use them, simply launch your maven command with a property like `-Dproperty=value` (i.e. `mvn license:check -Dlicense.header=src/etc/header.txt`)

All plugin configuration options are described in the [Detailed Maven documentation](#detailed-maven-documentation) but here are some details.

 - `useDefaultExcludes`: The default exclusion list can be found [here](https://github.com/mycila/license-maven-plugin/blob/master/src/main/java/com/mycila/maven/plugin/license/Default.java)

## Supported comment types ##

The plugin has been designed so that it is very easy to add new supports for new sorts of comment. The plugin currently support these types of comment:

 - `JAVADOC_STYLE` (Java-like comments): *.java, *.groovy, *.css, *.cs, *.as, *.aj, *.c, *.h, *.cpp

```
    /**
     * My comment
     */
```

 - `XML_STYLE` (XML-like comments): *.pom, *.xml, *.xhtml, *.mxml, *.dtd, *.xsd, *.jspx, *.fml, *.xsl, *.html, *.htm, *.kml, *.gsp, *.tld

```
	<!--
	    My comment
	-->
```

 - `DOUBLETILDE_STYLE` (APT-like comments): *.apt

```
	~~ My comment
```

 - `SCRIPT_STYLE` (Property file or shell comments): *.properties, *.sh, *.py, *.rb, *.pl, *.pm

```
	# My comment
```

 - `HAML_STYLE`: *.haml, *.scaml

```
	-# My comment
```

 - `BATCH` (Windows batch comments): *.bat, *.cmd

```
	@REM My comment
```

 - `TEXT` (Text like comments): *.txt

```
	====
	    My comment
	====
```

(4 spaces, then the lines of the header)

 - `DOUBLEDASHES_STYLE` (Sql like comments): *.sql, *.adb, *.ads, *.e

```
	--
	-- test comment
	--
```

 - `DYNASCRIPT_STYLE` (JSP like comments): *.jsp

```
	<%--
	    comment
	--%>
```

 - `FTL` (FreeMarker like comments): *.ftl

```
	<#--
	    comment
	-->
```

 - `FTL_ALT` (FreeMarker Alternative Syntax comments)

```
	[#ftl ...]
	[#--
	    comment
	--]
```

 - `SHARPSTAR_STYLE` (Velocity templates comments): *.vm

```
	#*
	    comment
	*##
```

 - `SEMICOLON_STYLE` (Assembler like comments): *.asm

```
	;
	; comment
	;
```

 - `BRACESSTAR_STYLE` (Delphi like comments): *.pas

```
	{*
	 * comment
	 *}
```

 - `APOSTROPHE_STYLE` (VisualBasic like comments): *.bas

```
	'
	' comment
	'
```

 - `EXCLAMATION_STYLE` (Fortran like comments): *.f

```
	!
	! comment
	!
```

 - `SLASHSTAR_STYLE` (JavaScript like comments): *.js

```
	/*
	 * comment
	 */
```

 - `DYNASCRIPT3_STYLE` (Coldfusion like comments): *.cfc, *.cfm

```
	<!---
	    comment
	--->
```

 - `PERCENT3_STYLE` (Erlang like comments): *.erl, *.hrl

```
	%%%
	%%% comment
	%%%
```

 - `EXCLAMATION3_STYLE` (Lisp like comments): *.el

```
	!!!
	!!! comment
	!!!
```

 - `LUA` (Lua like comments): *.lua

```
	--[[
	comment
	]]
```

 - `ASP` (Asp like comments): *.asp

```
	<%
	' comment
	%>
```

 - `PHP` (PHP comments): *.php

```
	/*
	 * comment
	 */
```

(inserted after the <?php> tag)

 - `DOUBLESLASH_STYLE` (often used comments style)

```
	//
	// comment
	//
```

*The plugin enables you to add any other mapping you want.* I.e., if you are developing a Tapestry web application, you may need to add license header in .jwc files and .application files. since these files are xml files, you only need to add in your project pom the following mapping for the license-maven-plugin:

{{{
<mapping>
    <jwc>XML_STYLE</jwc>
    <application>XML_STYLE</application>
</mapping>
}}}




= variable replacement in header =

You can define some variable in your header, and they will be replaced when the header file will be read. The values of the properties are taken first from the command line (java system properties), then from the plugin properties, then from the system properties.

See [Configuration the configuration reference guide] to see how to use it.


= Default excludes =

Patterns that are excluded by default when using `useDefaultExcludes` (default to true):

= Supported comment types =

There are all described in [http://code.google.com/p/license-maven-plugin/ the Home page]. The list contains:

`java, xml, properties, apt, batch, text, sql, jsp, ftl, ...`

= Default mappings =

The default mapping is built using the file extension and the style of comment to use. By default, the mapping between supported extensions and comment type contains the supported extensions [http://code.google.com/p/license-maven-plugin/wiki/SupportedFormats here]. You can customize the default mapping by providing your own one:

{{{
<mapping>
    <java>JAVADOC_STYLE</java>
    <groovy>JAVADOC_STYLE</groovy>
    <js>JAVADOC_STYLE</js>
    <css>JAVADOC_STYLE</css>
    <xml>XML_STYLE</xml>
    <dtd>XML_STYLE</dtd>
    <xsd>XML_STYLE</xsd>
    <html>XML_STYLE</html>
    <htm>XML_STYLE</htm>
    <xsl>XML_STYLE</xsl>
    <fml>XML_STYLE</fml>
    <apt>DOUBLETILDE_STYLE</apt>
    <properties>SCRIPT_STYLE</properties>
    <sh>SCRIPT_STYLE</sh>
    <txt>TEXT</txt>
    <bat>BATCH</bat>
    <cmd>BATCH</cmd>
    <sql>DOUBLEDASHES_STYLE</sql>
    <jsp>DYNASCRIPT_STYLE</jsp>
    <ftl>FTL</ftl>
    <xhtml>XML_STYLE</xhtml>
    <vm>SHARPSTAR_STYLE</vm>
    <jspx>XML_STYLE</jspx>
</mapping>
}}}

= Variable replacement =

If you have a header that contains variable like this one:

{{{
Copyright (C) ${year} ${user.name} <${email}>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
}}}

The plugin will try to replace them using the properties supplied in the command line, then those supplied in the POM, and then those from the system environment.

To test, you can launch the check goal in debug mode like this:

`mvn -X license:check -Dyear=2010`

Outputs for me:

{{{
Copyright (C) 2010 kha <my@email.com>
}}}

Notice that the year 2008 specified in the POM above has been overridden by the java property. And since the user.name is already a java system property, you don't need to specify it.

= Debugging, controlling the output =

The plugin let you control the output by the *`license.quiet`* property.

But to see if the plugin is working well, if your header is parsed correctly with properties, you may need to activate the Maven debug flag *-X* to see the plugin debug output.

Example: `mvn -X license:check`

= Changing header style definitions =

In license-maven-plugin, each header style is defined by patterns to detect it and also strings to insert it correctly in files. If we take for example the Javadoc style header definition. It is defined as follow:

{{{
<?xml version="1.0" encoding="ISO-8859-1"?>
<additionalHeaders>
    <javadoc_style>
        <firstLine>/**</firstLine>
        <beforeEachLine> * </beforeEachLine>
        <endLine> */</endLine>
        <!--skipLine></skipLine-->
        <firstLineDetectionPattern>(\s|\t)*/\*.*$</firstLineDetectionPattern>
        <lastLineDetectionPattern>.*\*/(\s|\t)*$</lastLineDetectionPattern>
        <allowBlankLines>false</allowBlankLines>
        <isMultiline>true</isMultiline>
    </javadoc_style>
</additionalHeaders>
}}}

And for XML:

{{{
<?xml version="1.0" encoding="ISO-8859-1"?>
<additionalHeaders>
    <javadoc_style>
        <firstLine><![CDATA[<!--\n]]></firstLine>
        <beforeEachLine>    </beforeEachLine>
        <endLine><![CDATA[-->]]></endLine>
        <skipLine><![CDATA[^<\?xml.*>$]]></skipLine>
        <firstLineDetectionPattern><![CDATA[(\s|\t)*<!--.*$]]></firstLineDetectionPattern>
        <lastLineDetectionPattern><![CDATA[.*-->(\s|\t)*$]]></lastLineDetectionPattern>
        <allowBlankLines>false</allowBlankLines>
        <isMultiline>true</isMultiline>
    </javadoc_style>
</additionalHeaders>
}}}

With the *headerDefinitions* option, you can redefine existing header styles and also add some if we do not support the styles you want yet. You just have to provide a list of *headerDefinition* containing a resource name. Like the header, the resource is searched on the file system, in the classpath of the project, the plugin and also as a URL.

See [AdvancedHeaders Advanced Headers configuration] for more information

= Working with multi-module projects =

here is an example of configuration you can have in a parent pom, when working in a multimodule project:

{{{
<plugin>
    <inherited>false</inherited>
    <groupId>com.mycila.license-maven-plugin</groupId>
    <artifactId>license-maven-plugin</artifactId>
    <version>1.4.0</version>
    <configuration>
        <header>${basedir}/etc/header.txt</header>
        <failIfMissing>true</failIfMissing>
        <aggregate>true</aggregate>
        <properties>
            <owner>Mathieu Carbou</owner>
            <year>${project.inceptionYear}</year>
            <email>mathieu.carbou@gmail.com</email>
        </properties>
        <excludes>
            <exclude>LICENSE.txt</exclude>
            <exclude>**/src/test/resources/**</exclude>
            <exclude>**/src/test/data/**</exclude>
        </excludes>
    </configuration>
    <executions>
        <execution>
            <id>check-headers</id>
            <phase>verify</phase>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
}}}


==================================




==============================================================


#summary Give an example of an additional header definition for .Net regions.

= Introduction =

This page will show you how you can define extended header definitions to feet your needs. The next example will define headers in a _region_ area allowed in C# source files:


{{{
<?xml version="1.0" encoding="ISO-8859-1"?>
<additionalHeaders>
    <csregion_style>
        <firstLine>#region LicenseEOL/**</firstLine>
        <beforeEachLine> * </beforeEachLine>
        <endLine> */EOL#endregion</endLine>
        <firstLineDetectionPattern>#region.*^EOL/\*\*.*$</firstLineDetectionPattern>
        <lastLineDetectionPattern>\*/EOL#endregion"</lastLineDetectionPattern>
        <allowBlankLines>true</allowBlankLines>
        <isMultiline>true</isMultiline>
    </csregion_style>
</additionalHeaders>
}}}

 * The _EOL_ string will be replaced with the proper end of line depending the file format your are processing.
 * We also have defined the _skipLine_ attribute to skip the region tags (which starts with a '#')
 * _allowBlankLines_ allows you to define if this header style supports blank lines in it or not. In example, in XML headers, you could have blank lines after the <!-- and before --> because XML delimiters delimit a multiline block. When you work with script style comments like in Ruby, Porperties files, the # character delimit a comment for only one line. So when you create the header, for it to be uniform, you place # on each line. So allowBlankLines will be false.
 * _isMultiline_ specifies if your header has tokens to delimit a multiline comment of if the tokens are a one-line comment. I.E.: XML style comments are multiline whereas script style comment where each line starts with # are not multiline

You now have to add this new header definition file to the plugin configuration. It is done as the following in your pom:

{{{
<headerDefinitions>
   <headerDefinition>yourdefinition.xml</headerDefinition>
</headerDefinitions>
}}}


You now have to add the new mapping for `*.cs` files to use this new header definition. It is done as the following in your pom:

{{{
<mapping>
    <cs>CSREGION_STYLE</cs>
</mapping>
}}}

If you need more information on the pom configuration, just read the [http://code.google.com/p/license-maven-plugin/w/edit/Configuration Configuration page].

And it should generate headers like:
{{{
#region License
/**
 * Copyright (C) 2008 http://code.google.com/p/license-maven-plugin/
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *         http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
#endregion
}}}



=============================================



#summary How to use license-maven-plugin
<wiki:toc max_depth="2" /> 
= license-maven-plugin configuration reference =

See [Configuration the license-maven-plugin configuration reference wiki page] to have for information about all the possible configuration options of this plugin !

= STEP 1: Set Maven 2 repository =

*license-maven-plugin is available in Maven Central Repo at http://repo1.maven.org/maven2/com/mycila/license-maven-plugin/ *

*to get the really latest releases and snapshots*

Since it can take some weeks before releases are uploaded in the central repo by the maven team, i provide a maven repository that you can use to get the plugin.

Add in your POM or settings.xml file the plugin repository mc-repo here. See explanations at http://code.google.com/p/mc-repo/wiki/HowToUse.

You should only need to add this:

{{{
<pluginRepository>
    <id>mc-release</id>
    <name>Local Maven repository of releases</name>
    <url>http://mc-repo.googlecode.com/svn/maven2/releases</url>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
    <releases>
        <enabled>true</enabled>
    </releases>
</pluginRepository>
}}}

and for snapshots

{{{
<pluginRepository>
    <id>mc-release</id>
    <name>Local Maven repository of releases</name>
    <url>http://mc-repo.googlecode.com/svn/maven2/snapshots</url>
    <snapshots>
        <enabled>true</enabled>
    </snapshots>
    <releases>
        <enabled>false</enabled>
    </releases>
</pluginRepository>
}}}

= STEP 2: Create a header file =

The plugin needs that you put a file on your project that contain the header, license or whatever text you want to see on the top of your source files. In the examples below, the file *header.txt* has the following content:

{{{
Copyright (C) ${year} ${user.name} <${email}>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
}}}

You can also provide for the header any valid URL or a resource from the classpath

== Be careful about line end ! ==

On Windows, lines end with CRLF (\r\n) whereas on Unix they end with LF (\n). If you apply a header file saved in Windows format to your files developed on Unix, you will end up with files having line ends like in Unix, except for the header part: you will have \r\n. The side effect is that in some Unix editors, you could see ^M characters at line ends for the header part.

The solution is very simple: you just have to convert your header with dos2unix. You can also convert all your project files like this:

 `for i in ```find src -type f | grep -v .svn | grep -v java```; do dos2unix $i; done`

 - Thanks to [http://code.google.com/p/license-maven-plugin/issues/detail?id=26 Erik Drolshammer's report]

= STEP 3: Check for missing headers (goal: check) =

To launch a check, simply add the plugin to your POM and issue:

*`mvn license:check -Dyear=2008 -Demail=myemail@company.com`*

{{{
<build>
    <plugins>
        <plugin>
            <groupId>com.mycila.license-maven-plugin</groupId>
            <artifactId>license-maven-plugin</artifactId>
            <configuration>
                <header>src/etc/header.txt</header>
            </configuration>
        </plugin>
    </plugins>
</build>
}}}

You can also automatically bind the check to the verify phase if you want a build to fail when missing headers are found. You just have to include the following declaration to check for missing headers, and then issue:

*`mvn verify -Dyear=2008 -Demail=myemail@company.com`*

{{{
<build>
    <plugins>
        <plugin>
            <groupId>com.mycila.license-maven-plugin</groupId>
            <artifactId>license-maven-plugin</artifactId>
            <configuration>
                <header>src/etc/header.txt</header>
            </configuration>
            <executions>
                <execution>
                    <goals>
                        <goal>check</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
}}}

If you want to bind to another phase, i.e. the test phase, you just have to declare the phase in the execution tag like this:

{{{
<build>
    <plugins>
        <plugin>
            <groupId>com.mycila.license-maven-plugin</groupId>
            <artifactId>license-maven-plugin</artifactId>
            <configuration>
                <header>src/etc/header.txt</header>
            </configuration>
            <executions>
                <execution>
                    <phase>test</phase>
                    <goals>
                        <goal>check</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
}}}

With this, you will then check the headers after the tests by doing *`mvn test  -Dyear=2008 -Demail=myemail@company.com`*

*Note:* The properties in the header and in the command line are optional. If you prefer, you can set directly the values in the header and not use properties. Also, you would prefer configuring the plugin for your needs to set properties in the maven POM. See [Configuration the license-maven-plugin configuration guide] to see all the possibilities of this plugin.

= STEP 4: Add missing headers (goal: format) =

This goal enables you to add or update existing license headers to put the one in the header file you have specified.

To launch it: *`mvn license:format -Dyear=2008 -Demail=myemail@company.com`* (having the configuration below)

{{{
<build>
    <plugins>
        <plugin>
            <groupId>com.mycila.license-maven-plugin</groupId>
            <artifactId>license-maven-plugin</artifactId>
            <configuration>
                <header>src/etc/header.txt</header>
            </configuration>
        </plugin>
    </plugins>
</build>
}}}





[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/1cff289591701ebe8f738c19916b60bd "githalytics.com")](http://githalytics.com/mycila/license-maven-plugin)
