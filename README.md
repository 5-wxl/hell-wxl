# hell-wxl
just another repository
package net;
import java.io.*;
import java.net.*;
public class Net {
	   ServerSocket server;
	   Socket client;
	   OutputStream out;
	   InputStream  in; 
    public void createServer(){//定义createServer方法
		   try{//创建Server对象  
			   server=new ServerSocket(5578);
			 	client=server.accept();  //等待客户端访问
			   //创建I/O通道
			    in=client.getInputStream();
			   out=client.getOutputStream(); 
			   }catch(Exception e){}   
	}
    public void createClient(){//定义createClient方法
		   try{//创建client对象 
			   client = new Socket("127.0.0.1",5578);
			    //创建I/O通道
			    in=client.getInputStream();
			   out=client.getOutputStream(); 
			   }catch(Exception e){}   
	}
    public String receive(){ //定义receive方法
    try{ //读取数据 
    	 byte s[]=new byte[90] ;
    	 in.read(s);
     return  new String(s);
        }catch(Exception eee){return null;}   	    
    }
    public void send(String send){ //定义send方法
  	      try{ //发送数据
          out.write(send.getBytes());
          }catch(Exception eee){eee.printStackTrace();}    
   }   
}
