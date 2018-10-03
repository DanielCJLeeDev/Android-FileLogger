
Android-FileLogger
============================

A general-purpose logging library with built-in support to save logs to file.

For performance concern, I/O operation is buffered and executed in background thread.


Usage
-----
```gradle
dependencies {
    compile 'com.github.bosphere.android-filelogger:filelogger:1.0.7'
}
```

Please refer to the sample app for more details.

```java
FL.init(new FLConfig.Builder(this)
        .logger(...)       // customise how to hook up with logcat
        .defaultTag("Default Tag")   // customise default tag
        .minLevel(FLConst.Level.V)   // customise minimum logging level
        .logToFile(true)   // enable logging to file
        .dir(directory)    // customise directory to hold log files
        .formatter(...)    // customise log format and file name
        .retentionPolicy(FLConst.RetentionPolicy.FILE_COUNT) // customise retention strategy
        .maxFileCount(FLConst.DEFAULT_MAX_FILE_COUNT)    // customise how many log files to keep if retention by file count
        .maxTotalSize(FLConst.DEFAULT_MAX_TOTAL_SIZE)    // customise how much space log files can occupy if retention by total size
        .build());
        
        
// overall toggle to enable/disable logging
FL.setEnabled(true);

// to log with default tag
FL.d("this is a debug message");

// to log with placeholder and interpolation
FL.d("this is a %s message", "debug");

// to log with specified tag
FL.d("Tag", "this is a %s message", "debug");

// to log exception
FL.e("Tag", throwable);
FL.e("Tag", throwable, "extra %s info", "debug");

```

Compatibility
-------------

API 9 (Android 2.3) and up

License
-------

Copyright 2018 Yang Bo

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
