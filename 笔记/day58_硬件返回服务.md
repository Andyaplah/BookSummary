1.JNI实现了应用程序对硬件的操作

思路是：应用程序中我们申明了本地方法，并通过System.loadLibrary("hardcontrol"); 来加载C库，loadLibrary的同时会调用C库中JNI_OnLoad方法，来注册本地方法，这个时候应用程序就可以通过调用申明的方法来调用C库中对应的方法，从而实现对硬件的访问



2.android系统没有采用上面这种方式,而是采用了硬件访问服务来操作硬件

（1）硬件访问服务，通过SystemServer来访问硬件，SystemServer通过loadlibrary来加载C库。

（2）同时C库的JNI_OnLoad函数被调用，里面分别调用硬件的JNI函数注册本地方法（JNI调用HAL层）。

（3）SystemServer对每个硬件，构造service，如：vibrator = new VibratorService(context);

（4）然后向ServiceManager里addService。如：ServiceManager.addService("vibrator", vibrator);

（5）应用程序获得service，然后调用里面的方法。
