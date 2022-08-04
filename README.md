# Richard Jeremy Githuba 115862  
# Remote Method Invocation Code Exercise

## 1) Create Remote Interface

```
import java.rmi.*;
public interface Adder extends Remote{

public int add(int x,int y)throws RemoteException;
}
```
## 2) Provide the implementation of the remote interface

```
import java.rmi.*;  
import java.rmi.server.*;  
public class AdderRemote extends UnicastRemoteObject implements Adder{  
AdderRemote()throws RemoteException{  
super();  
}  
public int add(int x,int y){return x+y;}  
}  
```

## 3) create the stub and skeleton objects using the rmic tool

```
rmic AdderRemote  
```

## 4) Start the registry service by the rmiregistry tool

```
rmiregistry 1099  
```

## 5) Create and run the server application

```
import java.rmi.*;  
import java.rmi.registry.*;  
public class MyServer{  
public static void main(String args[]){  
try{  
Adder stub=new AdderRemote();  
Naming.rebind("rmi://localhost:1099/sonoo",stub);  
}catch(Exception e){System.out.println(e);}  
}  
}  
```

## 6) Create and run the client application

```
import java.rmi.*;  
public class MyClient{  
public static void main(String args[]){  
try{  
Adder stub=(Adder)Naming.lookup("rmi://localhost:1099/sonoo");  
System.out.println(stub.add(34,4));  
}catch(Exception e){}  
}  
}  
```





