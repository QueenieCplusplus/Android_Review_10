# Android_Review_10
Retrofit Network and uses-permission

1. add dependencies using implementation method called in path app/build.gradle

       dependencies {

         // networking using retrofit2
            implementation 'com.squareup.retrofit2:retrofit:2.9.0'

         // coroutines-adapter using retrofit2
            implementation 'com.jakewharton.retrofit:retrofit2-kotlin-coroutines-adapter:0.9.2'
            
         // converter from retrofit to moshi
            implementation 'com.squareup.retrofit2:converter-moshi:2.9.0'

         // json fomat parsing using moshi
            def moshi_version = "1.9.3"
            implementation "com.squareup.moshi: moshi: $moshi_version"
            implementation "com.squareup.moshi: moshi-kotlin: $moshi_version"
            kapt "com.squareup.moshi: moshi-kotlin-codegen: $moshi_version"

       }

2. add uses-permission tag in AndroidManifest.xml

    
