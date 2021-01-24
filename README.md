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
    
4. code an object as a Main Entry Point for Network Access using objName.interfaceName.methodCalled(). and using Retrofit.Builder().chainMethodCalled().create(ServiceInterface)

       // go to app/src/main/java/com/example/android/katesapp/network/Service.kt
       
       package com.example.android.katesvideoapp.network
       
       [network module]
       import retrofit2.Retrofit
       
       [Byte ftecher module]
       import retrofit2.http.GET
       
       [coroutines module]
       // TODO:
       // see Android_Rewiew_12
       
       [converter module]
       import retrofit2.converter.moshi.MoshiConverterFactory
       
       
       // object as a Main Entry Point for Network Access.
       // called `objName.interfaceName.methodCalled()`
       
       
       interface Service {
       
              @GET("bytesGetter")
              // TODO：Android_Rewiew_1
              // 回傳的型別
              suspencd fun getPlayer(): 回傳的型別 // 介面的方法沒有參數，故沒有建構子。
       
       }
       
       
       object Network {
       
             //放入 url 字串 
             parivate val rtf = Retrofit.Builder().baseUrl("").addConverterFactory(MoshiConverterFactory.create()).build()
       
             val bytesGetter = rtf.create(Service::class.java)
       
       
       }
       
       
5. Data format Transferer. It is responsible for parsing the response from server, and formatting obj to server, anyway this customed tool is used by domain obj which is defined in Android_Review_11.
 
       // go to app/src/main/java/com/example/android/katesapp/network/DataConverter.kt
       
       package com.example.android.katesvideoapp.network
       
       [db & domain module]
       // TODO: see Android_Review_11
       
       [converter module]
       import com.square.moshi.JsonClass
       
       
              // VideoHolder
       /*
          {
            "videos": []
          }
       
       */
       
       
       // httpResult 
       @JsonClass(generateAdapter = true)
       data class Video(
              
              val title: String,
              val des: String,
              val url: String,
              val updated: String,
              val falesCaption: String?, // nullable
              val thumbnail: String // 縮圖
                 
       )
       
   
       
       // TODO
       // after Android_Review_11 is done.
       // httpResult - dbObj converter
       
       /* fun methodCalled(): List<Video> {
       
             return videos.map {
             
                 Video(
                 
                     title = it.title
                     des = it.des
                     url = it.url
                     updated = it.updated
                     thumbnail = it.thumbnail
                 
                 )
             
             }
       
       
       }*/
      
 
6. app's architecture =>


              app - db (data src fm Room)
                  - domain (see Android_Review_11, data src fm web server)
                  - repo (mediators for diff data src)
                  - viewmodels (see Android_Review_12, to resolve the problems from I/O threads and UI main thread using coroutines instead of threads)
           

7. today's tip (bit and Byte)

   bit （位元）為資料傳輸單位，byte （位元組） 為檔案大小單位。
   
8. today's tip (abstract class and interface)

   訊息不足夠的描繪對象適用於『抽象類別』。
   而『介面』屬於 『抽象類別』，抽象類別不屬於介面。
   
   Java 語言中，類支援多重導入 implements 介面，不支持派生類別多重繼承 extends 抽象類別。
   派生類 is a 抽象類別，派生類 as a 介面。
   
   抽象類別的限制：
   
   (1) 抽象類別無法用 new 產生實例物件。
   
   (2) 抽象類別需要宣告，不需要實作。
   
   (3) 繼承的子類別需要實做繼承來的方法。
   
   介面的限制：
   
   (1) 介面的方法沒有參數，所以沒有建構方法。
   
   (2) 介面中的資料成員為常數，故需要初始化。
   
   (3) 介面的方法必須為抽象或是 public。
   
   洋娃娃女演員本質上是能演繹出取得和丟的行為，同時具有人類的表情表達功能，設計意圖如下：
   
       abstract class Action {
       
              abstract void catch(param);
              abctract void throw(param);
       
       }
       
       interface HumanFacialAct {
       
              void smile();
              void yell();
              void cry();
       
       }
       
       interface RobotAction {
       
              void walk();
              void sway();
       
       }
       
       class DollyActress extends Action implements HumanFaciaAct, RobotAction {
       
              void catch(param){body}; 
              void throw(param){body};
              void smile(); 
              void walk();
       
       }
 
9. today's tip (::)

   class ref
   
   https://stackoverflow.com/questions/47400942/what-does-mean-in-kotlin
       
       
10. today's tip (suspend fun)

  plz wait...


