# JEAF UML2 Libraries

Runtime of [Eclipse UML2](https://projects.eclipse.org/projects/modeling.mdt.uml2) as used by [JEAF Generator](https://www.jeaf-generator.io) and [JEAF Xpand](https://github.com/anaptecs/jeaf-xpand).

Eclipse UML2 is only published to Eclipse p2 update sites, not to Maven Central. This project builds the runtime bundles with Maven and publishes them to Maven Central.

The code is based on Eclipse UML2 5.6.1 (repository [eclipse-uml2/uml2](https://github.com/eclipse-uml2/uml2), commit `23371ccc15a28bc830c073ccd1a80e97945f59c6`, release of 2026-06 with bundle qualifier `v20260601-1345`).

## Modules

| Artifact (`com.anaptecs.jeaf.uml2libs`) | Eclipse UML2 bundle | Content |
| --------------------------------------- | ------------------- | ------- |
| `uml2-common`                | `org.eclipse.uml2.common` 2.6.0                | Common utilities |
| `uml2-types`                 | `org.eclipse.uml2.types` 2.6.0                 | Primitive types |
| `uml2-uml`                   | `org.eclipse.uml2.uml` 5.6.0                   | UML metamodel |
| `uml2-uml-profile-standard`  | `org.eclipse.uml2.uml.profile.standard` 1.6.0  | UML standard profile |
| `uml2-uml-resources`         | `org.eclipse.uml2.uml.resources` 5.6.0         | UML libraries, profiles and metamodels |

All artifacts have the version of the Eclipse UML2 release. EMF is taken from Maven Central.

Package names are the ones of Eclipse UML2.

## Differences to Eclipse UML2

- Sources and resources are taken from the bundles in the Eclipse UML2 repository (`src` and the files of `bin.includes`).
- Built with Maven as plain JAR files instead of OSGi bundles with Tycho. Eclipse signatures and OSGi manifests are not included. `org.eclipse.core.runtime` is an optional dependency, as it is only needed within Eclipse.
- `ClassifierOperations.allSlottableFeatures(...)`: additional cast to `Collection<?>`, as `javac` does not accept the cast that is accepted by the Eclipse compiler. Behavior is unchanged.
- `about.mappings` contains the placeholder `${buildId}` instead of the build ID of the Eclipse build.

## License

Eclipse Public License 2.0 (see [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md)), as Eclipse UML2 itself.
