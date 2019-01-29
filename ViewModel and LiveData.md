# ViewModel and LiveData 引用
LiveData 是一个可以保存数据和观察数据变化的组件。它是被设计用来在ViewModel中保存数据，LiveData只是一个普通的数据类型，
但是当数据发生变化时，它能够通知其观察者。

添加依赖
```
dependencies {
    // ViewModel and LiveData
    implementation "android.arch.lifecycle:extensions:1.1.1"
    // alternatively, just ViewModel
    implementation "android.arch.lifecycle:viewmodel:1.1.1"
    // alternatively, just LiveData
    implementation "android.arch.lifecycle:livedata:1.1.1"
    
    // 这个是用来生成代码的库,自动生成一些代码避免使用反射来提高性能。
    annotationProcessor "android.arch.lifecycle:compiler:1.1.1"
}
```
