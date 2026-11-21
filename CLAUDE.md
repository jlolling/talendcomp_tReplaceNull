# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

Talend component tReplaceNull: replaces null values.
User-facing behaviour and parameters are described in the manuals in `doc/`.

## Build

```bash
mvn clean package                      # test, assemble component(s), copy them to ${custom_component_folder}
```

No compiler level set in the pom (Maven default); `cimt-talendcomp-maven-plugin` 3.1. `custom_component_folder` is defined in `~/.m2/settings.xml`.

## Structure

- `src/main/components/<Name>/`: `<Name>_java.xml` (descriptor), `*.javajet` (code-generation templates), `<Name>_messages.properties` (labels, `LONG_NAME` required) and the icon. A parameter change usually touches all three.
- Generated at `package`, do not hand-edit: the `<IMPORTS>` block and HEADER `VERSION`/`RELEASE_DATE` in `_java.xml`, and jars in the component folders. Bump the version in `pom.xml`.
- There is no Java library: all logic lives in the javajet templates.
- The pom's artifactId `cimt-talendcomp-flatfileimport` is a copy-paste leftover, not this component's name.
