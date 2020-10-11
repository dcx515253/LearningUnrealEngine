2020-09-10_19:55:50

# Modules

A module is a collection of C++ files that are compiled and linked together into a library.
The C++ files are stored in a directory for the module along with a `<ModuleName>.Build.cs`.
The `Build.cs` file describe how the module is to be compiled.

The engine is built up from a large collection of modules.
Projects and plugins can also contain modules.

A module is declared in the owning project's or plugin's `.upoject` or `.uplugin` file.
The `Modules` attribute is an array that contains `Module` elements.
A `Module` element contains at least `Name`, `Type`, and `LoadingPhase`.
`Name` can be anything.
`Type` is one of `Runtime`, `Developer(Tool?)`, or `Editor`. There are a few more.
`LoadingPhase` is one of `Default`, ...?
Can also have `WhitelistPlatforms` and `BlacklistPlatforms`.

[[2020-09-15_21:10:32]] [Module types](./Module%20types.md)

A module consists of a private part and public part.
The private part can only be used by the module itself.
The public part can be used by other modules as well.
A module using functionality provided by another module is called a dependency.
The public part is stored in the `<ModuleName>/Public` directory.
The private part is stored in the `<ModuleName>/Private` directory.
For simple modules this is exactly the `.h`/`.cpp` separation.
But modules may place source files differently.

Classes defined within a module should be decorated with the module's `*_API` macro.
This exports the class from the module so that it can be used by other modules.
For example: `class MYMODULE_API UMyClass : public UObject`.
The definition for the macro is automatically created by the engine.

Example module file system organization, for a module named `MyFirstModule`:
```
MyFirstModule
├── MyFirstModule.Build.cs
├── Private
│   └── MyFirstModule.cpp
└── Public
    └── MyFirstModule.h
```

[[2020-09-10_19:42:18]] [Code projects](./Code%20projects.md)  
[[2020-09-15_17:27:33]] [Plugins](./Plugins.md)  
[[2020-09-15_21:10:32]] [Module types](./Module%20types.md)  