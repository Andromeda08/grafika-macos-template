## Számítógépes Grafika Template macOS felhasználók számára
A projekt a CMake build tool segítségével fordítható.  
### Függőségek telepítése
- **Xcode command line tools** (compiler, make, git, stb..)  
  `xcode-select --install`
- **CMake** *(CLion használata esetén nem szükséges)*
  - Homebrew: `brew install cmake`
  - [A CMake weboldalról](https://cmake.org/)
- Az `OpenGL` és `GLUT` könyvtárakat nem kell telepítenünk.  
### Egyéb
#### `OpenGL` és `GLUT` deprecation
Mivel ez a két könyvtár elalvultként van megjelölve fordításkor rengeteg ezzel kapcsolatos "hibával" találkozhatunk. Az olvashatóbb output érdekében érdemes definiálni a `GL_SILENCE_DEPRECATION` makrót projekt szinten *(cmake segítségével így)*:  
```
target_compile_definitions(${PROJECT_NAME} PRIVATE GL_SILENCE_DEPRECATION)
```
#### Fordítás `g++` segítségével
```console
g++ src/skeleton.cpp src/framework.cpp -o Skeleton -framework GLUT -framework OpenGL -std=c++11
```
#### Xcode használata 
[CMake segítségével generálható Xcode projekt is.](https://cmake.org/cmake/help/v3.0/manual/cmake-generators.7.html)
```console
cmake -G Xcode <CMakeLists.txt-t tartamazó mappa>
```
#### **Disclaimer: Framework fájlok**
Arra nem tudok garanciát vállalni, hogy a `framework.h` és `framework.cpp` fájlok naprakészek a tárgyoldalon találhatóakhoz képest. A template használata előtt érdemes frissíteni ezeket a fájlokat.
#### **Disclaimer: Intel vs Apple Silicon**
Egy `Intel` alapú mac-en csináltam és használtam ezt a templatet. Tudomásom szerint az új `ARM` alapú rendszereken is működőképesnek kéne lennie, de ezért nem tudok garanciát válalni.
