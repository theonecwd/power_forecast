# NDK_PROJECT_PATH=null
1. build.gradle文件中添加
```
    android {  
        ...  
      
        sourceSets.main {  
            jni.srcDirs = []  
            jniLibs.srcDir 'src/main/libs'  
        }  
      
    }  
```

2. src/main/jni目录下添加空文件

```
util.c
empty.cpp
```


