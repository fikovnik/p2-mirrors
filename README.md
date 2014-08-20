# p2-mirrors


A maven project that creates a local mirror of bunch of Eclipse P2 repositories using the [tycho-p2-extras-plugin](https://wiki.eclipse.org/Tycho/Additional_Tools#mirror_goal).
The idea is to speed up local [tycho](https://www.eclipse.org/tycho/) builds.

To use it simply execute

```
$ mvn install
```

To use the mirrors in a maven, register the mirros in the local `~/.m2/settings.xml` file:

```
<?xml version="1.0" encoding="UTF-8"?>
<settings>
  <mirrors>
    
    <mirror>
      <id>local-eclipse-juno</id>
      <mirrorOf>eclipse-juno</mirrorOf>
      <url>file:///<path to this repository>/p2-mirrors/repository/eclipse-juno</url>
      <layout>p2</layout>
      <mirrorOfLayouts>p2</mirrorOfLayouts>
    </mirror>
    
    <mirror>
      <id>local-scala-ide-e38</id>
      <mirrorOf>scala-ide-e38</mirrorOf>
      <url>file:///<path to this repository>/p2-mirrors/repository/scala-ide-e38</url>
      <layout>p2</layout>
      <mirrorOfLayouts>p2</mirrorOfLayouts>
    </mirror>
    
    <!-- ... -->
  </mirrors>
</settings>
```

In the project `pom.xml` the official repositories are listed and maven will figure out what to use.
