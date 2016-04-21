### **Пример по теме “Java. Синхронизация”**

```java
class Callme {
	synchronized void call(String msg){
		System.out.print("["+msg);
		try{Thread.sleep(1000);
		}catch(Exception e){}
		System.out.print("]");System.out.println("");
		}
	}
class Caller implements Runnable{
	String msg;
	Callme target;
	public Caller(Callme t, String s){
		target = t;
		msg = s;
		new Thread(this).start();
	}
	public void run(){
		target.call(msg);
	}
 
}
public class Sync {
	public static void main(String a[]){
		Callme target = new Callme();
		new Caller(target, "Hello");
		new Caller(target, "Synchronized");
		new Caller(target, "World");
	}
 
}
```
