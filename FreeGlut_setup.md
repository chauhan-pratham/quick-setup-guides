# **OpenGL + FreeGLUT Setup Guide for Windows 11**

This guide walks you through setting up OpenGL with FreeGLUT on a Windows 11 system.

---

## **Step 1: Install MSYS2**

1. Download MSYS2 from the official [MSYS2 website](https://www.msys2.org/). Follow the installation instructions provided there.
2. Open the MSYS2 terminal after installation.

---

## **Step 2: Install OpenGL and FreeGLUT**

To install the required OpenGL libraries, execute the following command in the MSYS2 terminal:

```sh
pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-freeglut mingw-w64-x86_64-mesa
```

---

## **Step 3: Add MSYS2 to System PATH**

1. Add MSYS2 to the system's `PATH` environment variable:
   - Go to **Control Panel** → **System** → **Advanced system settings**.
   - Click on **Environment Variables**.
   - Edit the `Path` variable and add the following directory:
     ```
     C:\msys64\mingw64\bin
     ```
2. Save and close the settings.

---

## **Step 4: Write and Save Your Code**

1. Use the FreeGLUT header:
   ```cpp
   #include <GL/freeglut.h>
   ```
   (Do not use `#include <GL/glut.h>`, as FreeGLUT is being used.)
2. Save your code with the filename `main.cpp`. Example code:

```cpp
#include <GL/freeglut.h>

void display() {
    glClear(GL_COLOR_BUFFER_BIT);
    // Add your rendering code here
    glFlush();
}

int main(int argc, char** argv) {
    glutInit(&argc, argv);
    glutCreateWindow("OpenGL FreeGLUT Example");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}
```

---

## **Step 5: Compile the Program**

Compile the code using the following command in your MSYS2 terminal:

```sh
gcc main.cpp -o main -lfreeglut -lglu32 -lopengl32
```

---

## **Step 6: Run the Program**

You can run the program in various ways based on your input requirements:

- **Standard Execution**:
  ```sh
  ./main.exe
  ```
- **Console-based Input** (e.g., for `cin`, `scanf`):
  ```sh
  ./main.exe
  ```
- **Input Redirection**:
  ```sh
  ./main.exe < input.txt
  ```
- **Command-Line Arguments**:
  ```sh
  ./main.exe 0.5 0.3 0.8
  ```

Congratulations! Your OpenGL + FreeGLUT environment is now set up and ready to use.

---

## **Additional Commands for Advanced Setup**

1. Install GLFW for additional functionality:
   ```sh
   pacman -S mingw-w64-ucrt-x86_64-glfw
   ```
2. Install GCC, GLAD, and GLM libraries for advanced OpenGL:
   ```sh
   pacman -S mingw-w64-ucrt-x86_64-gcc
   pacman -S mingw-w64-ucrt-x86_64-glad
   pacman -S mingw-w64-ucrt-x86_64-glm
   ```
3. Navigate to your project directory:
   ```sh
   cd path_to_your_directory
   ```
4. Compile your `main.cpp` with GLAD and GLFW:
   ```sh
   g++ main.cpp /ucrt64/lib/glad.c -o main.exe -I/ucrt64/include -L/ucrt64/lib -lglfw -lopengl32
   ```
