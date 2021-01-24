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

       <?xml encoding="utf-8" ?>
       
       <manifest
          package="com.example.android.katesappvideoapp"
       >
       
          <uses-permission
              android:name="android.permission.INTERNET"
          >
          
          <application>
          
              <activity
                 android:name="UI.activity_main_katesVideoApp"
              >
              
                  <intent-filter>
                  
                     <action/>
                     <category/>
                     
                  </intent-filter>
              
              </activity>
          
          </appliaction>
       
       </manifest>

3. databind with UI and code.

       // go to app/src/main/java/com/example/android/katesvideoapp/UI/KatesVideoAppMainActivity.kt
       
       package com.example.android.katesvideoapp.ui
       
       [default module]
       import android.os.Bundle
       import androidx.appcompat.app.AppCompatActivity
       
       [R]
       import com.example.android.katesvideoapp.R
       
       class KatesVideoAppMainActivit: AppComaptActivity(){
       
              override fun onCreate(savedInstanceState: Bundle?){
              
                     super.onCreate(savedInstanceState)
                     setContentView(R.layout.activity_main_katesVideoApp)
              
              }
       
       }
       
          // content is displayed by Fragment
          // go to app/src/main/java/com/example/android/katesvideoapp/ui/KatesVideoAppFragment.kt
          // see fragment_katesVieoApp.xml and katesvideoapp_item.xml 
          
       package com.example.android.katesvideoapp.ui
       
       [modules to be imported]
       
       
       
       // show a list of choices using RecyclerView component
       
       class KatesVideoAppFragment: Fragment(){
       
       
            // TODO : see Android_Review_11
            // data defined hereby
            
            // TODO : see Android_Review_13
            // viewModelAdapter
            
            overrdie fun onViewCreated(v: View, savedInstanceState: Bundle?){
            
              super.onViewCreated(v, avedInstanceState )
              
              // TODO : see Android_Review_13
              // viewModel's oberserve method called
              // render viewModelAdapter
            
            }
            
            
            override fun onCreatedView(inflater: LayoutInflater?, container: ViewGroup?, savedInstanceState: Bundle?): View? {
            
            
                // TODO today
                // databinding hereby
                
                // val binding = waith to defined
                
                // render binding.root
                
                // TODO today
                // Network Error Observer and Catcher
            
            
            }  
       
       
       }
       
       // TODO : see Android_Review_13
       // an Adapter class inherited from RecyclerView.Adapter<DevByteViewHolder> 
    
4. code an object as a Main Entry Point for Network Access.

       // go to app/src/main/java/com/example/android/katesapp/network/Service.kt
       
       package com.example.android.katesvideoapp.network
       
       [network module]
       import retrofit2.Retrofit
       
       [Byte ftecher module]
       import retrofit2.http.GET
       
       [adapter module]
       // TODO:
       // see Android_Rewiew_13
       
       [coroutines module]
       // TODO:
       // see Android_Rewiew_12
       
       // object as a Main Entry Point for Network Access.
       // called `objName.interfaceName.methodCalled()`
       
       object Network {
       
       
       }
       
       interface Service {
       
       
       }
       


5. today's tip (bit and Byte)

   bit （位元）為資料傳輸單位，byte （位元組） 為檔案大小單位。
   
6. today's tip (abstract class and interface)

   訊息不足夠的描繪對象適用於『抽象類別』。
   而『介面』屬於 『抽象類別』，抽象類別不屬於介面。
   
   Java 語言中，類支援多重導入 implements 介面，不支持派生類別多重繼承 extends 抽象類別。
   
