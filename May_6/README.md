### 以下程序的输出结果是
#### 1.
```
class Base {
    final public void show() {
       System.out.println("Base::show() called");
    }
}
  
class Derived extends Base {
    public void show() {			//报错，被final修饰的方法不能被重写
       System.out.println("Derived::show() called");
    }
}
  
class Main {
    public static void main(String[] args) {
        Base b = new Derived();
        b.show();     
    }
}
```

#### 2.
```
class Base {
    public static void show() {
       System.out.println("Base::show() called");
    }
}
  
class Derived extends Base {
    public static void show() {
       System.out.println("Derived::show() called");
    }
}
  
class Main {
    public static void main(String[] args) {
        Base b = new Derived();;
        b.show();              //报错，不能通过实例访问静态方法
    }
}
```

#### 3.
```
class Base {
    public void Print() {
        System.out.println("Base");
    }         
}
 
class Derived extends Base {    
    public void Print() {
        System.out.println("Derived");
    }
}
 
class Main{
    public static void DoPrint( Base o ) {
        o.Print();   
    }
    public static void main(String[] args) {
        Base x = new Base();
        Base y = new Derived();
        Derived z = new Derived();
        DoPrint(x);			//Base
        DoPrint(y);			//Derived
        DoPrint(z);			//Derived
    }
}
```

#### 4.

```
class Base {
    public void foo() { System.out.println("Base"); }
}
  
class Derived extends Base {
    private void foo() { System.out.println("Derived"); } 
}
  
public class Main {
    public static void main(String args[]) {
        Base b = new Derived();
        b.foo();		//报错，子类重写访问修饰符比父类低
    }
} 
```

#### 5.
```

public class NewClass { 
	public static class superclass { 
		static void print() 
		{ 
			System.out.println("print in superclass."); 
		} 
	} 
	public static class subclass extends superclass { 
		static void print() 
		{ 
			System.out.println("print in subclass."); 
		} 
	} 

	public static void main(String[] args) 
	{ 
		superclass A = new superclass(); 
		superclass B = new subclass(); 
		A.print(); 			//print in superclass.
		B.print(); 			//print in subclass.
	} 
} 
```
#### 6.
```

public class NewClass { 
	public static class superclass { 
		void print() 
		{ 
			System.out.println("print in superclass."); 
		} 
	} 

	public static class subclass extends superclass { 
		@Override
		void print() 
		{ 
			System.out.println("print in subclass."); 
		} 
	} 

	public static void main(String[] args) 
	{ 
		superclass A = new superclass(); 
		superclass B = new subclass(); 
		A.print(); 			//print in superclass.
		B.print(); 			//print in subclass.
	} 
} 
```

#### 7.
```
class ClassOne
{ 
    protected void getData() 
    { 
        System.out.println("Inside ClassOne");
    } 
} 
class ClassTwo extends ClassOne
{ 
    protected void getData() 
    { 
        System.out.println("Inside ClassTwo");
    } 
} 
  
public class Test 
{ 
    public static void main(String[] args) 
    { 
        ClassOne obj = new ClassTwo();
        obj.getData(); 			//Inside ClassTwo
    } 
} 
```

#### 8.
```
class Test 
{ 
    void myMethod() 
    { 
        System.out.println("Test");
    } 
} 
class Derived extends Test
{ 
    void myMethod() 
    { 
        System.out.println("Derived");
    } 
      
    public static void main(String[] args) 
    { 
        Derived object = new Test(); 
        object.myMethod(); 		//报错，父类引用无法转为子类对象
    } 
} 
```
#### 9.
```
class ClassOne
{ 
    protected void getData() 
    { 
        System.out.println("Inside ClassOne");
    } 
} 
class ClassTwo extends ClassOne
{ 
    protected void getData() 
    { 
        System.out.println("Inside ClassTwo");
    } 
      
    protected void getValue() 
    { 
        System.out.println("ClassTwo");
    } 
} 
  
public class Test 
{ 
    public static void main(String[] args) 
    { 
        ClassOne obj = new ClassTwo();
        obj.getValue();  		//报错，ClassOne中没有getValue()方法
    } 
} 
```