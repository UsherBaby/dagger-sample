### Dagger Sample: Basic demonstration on how to include Dagger 2.11-rc2 with an Android project
[![Build Status](https://img.shields.io/travis/ashdavies/dagger-sample.svg)](https://travis-ci.org/ashdavies/dagger-sample)
[![License](https://img.shields.io/badge/license-apache%202.0-blue.svg)](https://github.com/ashdavies/dagger-sample/blob/master/LICENSE.txt)

NOTE:

In kotlin 
```
@Module
abstract class ApplicationModule {

  @Binds
  public abstract Application application(MainApplication mainApplication);
}
```
and 
```
public class MainApplication extends DaggerApplication {

  @Override
  protected AndroidInjector<? extends DaggerApplication> applicationInjector() {
    return DaggerApplicationComponent.builder().create(this);
  }
}
```
cause MainApplication bound mutiple time error

solution:
change 
```DaggerApplicationComponent.builder().create(this);``` 
to
```DaggerApplicationComponent.builder().build();```

or remove 
```
@Module
abstract class ApplicationModule {

  @Binds
  public abstract Application application(MainApplication mainApplication);
}
```

