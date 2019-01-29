# AndroidViewModel vs ViewModel
AndroidViewModel 和 ViewModel 的关系
AndroidViewModel extends ViewModel，Subclasses must have a constructor which accepts Application as the only parameter.
AndroidViewModel 是 ViewModel的子类，他有一个只有一个 Application 参数的构造函数，如果你需要在 viewmodel 中使用上下文则使用 AndroidViewModel 否者就用 ViewModel。参见 stackoverflow的回答：
* [AndroidViewModel vs ViewModel](https://stackoverflow.com/questions/44148966/androidviewmodel-vs-viewmodel) 
* [What is the Difference between AndroidViewModel and ViewModel in Android Architecture Components?](https://stackoverflow.com/questions/46730113/what-is-the-difference-between-androidviewmodel-and-viewmodel-in-android-archite?rq=1)

源码如下：
```
package android.arch.lifecycle;

import android.annotation.SuppressLint;
import android.app.Application;
import android.support.annotation.NonNull;

/**
 * Application context aware {@link ViewModel}.
 * <p>
 * Subclasses must have a constructor which accepts {@link Application} as the only parameter.
 * <p>
 */
public class AndroidViewModel extends ViewModel {
    @SuppressLint("StaticFieldLeak")
    private Application mApplication;

    public AndroidViewModel(@NonNull Application application) {
        mApplication = application;
    }

    /**
     * Return the application.
     */
    @NonNull
    public <T extends Application> T getApplication() {
        //noinspection unchecked
        return (T) mApplication;
    }
}

public abstract class ViewModel {
    /**
     * This method will be called when this ViewModel is no longer used and will be destroyed.
     * <p>
     * It is useful when ViewModel observes some data and you need to clear this subscription to
     * prevent a leak of this ViewModel.
     */*
    @SuppressWarnings("WeakerAccess")
    protected void onCleared() {
    }
}

```
