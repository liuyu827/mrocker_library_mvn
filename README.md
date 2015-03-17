# mrocker_library_mvn 使用方法

##集成方法


####1.配置maven地址
	repositories {
    	maven{
        	url "https://github.com/liuyu827/mrocker_library_mvn/raw/master"
    	}
    }
    
####2.依赖当前maven库
	dependencies {
    	compile 'com.mrocker.library:common:1.1.0'
	}
	
	
##版本说明	
- v1.1.0
 
	1.在加载数据时，添加缓存机制，调用例子：
		
		LibraryLoad.load(context, "http://")
                .localFirst()
                .setExceedTime(10000)
                .asGet()
                .setCallback(new LibraryLoadingCallback() {
                    @Override
                    public void onCompleted(Throwable e, boolean local, boolean loadNet, int code, String result) {
                        //todo 
                    }
                });
                
    `localFirst()`代表优先加载本地数据。   
    `setExceedTime(10000)`代表缓存的时间。  
    
    
    2.联网回调方法做了修改：
      
	原来  
	`public void onCompleted(Exception e, int code, String result)`  方法废弃，

	使用新的方法
    
    `onCompleted(Throwable e, boolean local, boolean loadNet, int code, String result)`，  
	`local`代表是否为本地数据。  
	`loadNet`代表加载完本地数据后是否会再加载网络数据。如果已经获取网络数据，则此值为false。

           
    
	

