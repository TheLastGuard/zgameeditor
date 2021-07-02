# ZExternalLibrary {#ZExternalLibrary}

Definition of interface, consisting of functions and constants, to external .DLL
or Android shared .SO library. After defining in ZExternalLibrary, it is
possible to call external functions and defined constants from expressions.

External links:
[List of external libraries and related discussions in the Forum](http://www.emix8.org/forum/viewforum.php?f=10)

## Properties

@dl

@dt ModuleName @dd Name of library file. Extension ".dll" can be omitted. For
instance, "bass.dll", or just "bass". For Android libraries, it must be full
file name, including the relative directory, for instance, "./bass.so".

@dt CallingConvention @dd The calling-convention used by the dll/shared object
library.

- Stdcall
- Cdecl

For details see
[Wikipedia article](https://en.wikipedia.org/wiki/X86_calling_conventions).

@dt BeforeInitExp @dd This @ref ScriptingLanguage "expression" runs before the
ZExternalLibrary loads, so you can set ModuleName here based on the ANDROID
constant. See the OpenGL component in the library for an example:

    if(ANDROID)
      this.ModuleName="libGLESv1_CM.so";

Value of this property is specified in @ref CodeEditor "Code editor".

@dt Source @dd Declare library functions with the following syntax:

@syn{<return type> <function name>(<type> <name>, <type> <name>, ...) \{\}}

Value of this property is specified in @ref CodeEditor "Code editor".

See example project ModPlay in Projects folder.

Here is a short list on how to convert parameter types between C/C++ types used
in DLL and ZGameEditor types:

| C/C++ type                         | ZGameEditor type          |
| ---------------------------------- | ------------------------- |
| int, word, longword, byte, bool    | int                       |
| byte                               | byte                      |
| float                              | float                     |
| LPCTSTR, char\*                    | string                    |
| QWORD, INT64                       | define two int-parameters |
| pointers to structures and objects | xptr                      |

@note External function for Android library can take maximum up to 16
parameters.

@dt DefinitionFile @dd If specified, the definition of external functions is not
given in the Source property, but in a file specified here. The file must be
placed in the `<zge_install_dir>\Lib` directory. Fro example, see the "OpenGL
4.0 graphics" and "Bullet 3D physics library" libraries from built-in library of
components.

@dlx
