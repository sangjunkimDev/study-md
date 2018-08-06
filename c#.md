# C# 공부

### 정의
- 개체 지향 언어(객체 지향 언어)
- 구성 요소 지향 언어
- 소스 파일 확장자는 .cs
- 기본 접근 제한자는 private

### 자바 vs C# 1 (확장자, package)
자바  |  C#
--|--
.java  |  .cs
``package test.test1;``  |  ``namespace Test.Test1 {...}``
``import test.test1;``  |  ``using Test.Test1;``
``import test.*;``  |  ``using Test;``

### 자바 vs C# 2 (자료형)
자바  |  C#
--|--
boolean  |  bool
byte  |  byte, sbyte
char  |  char
short  |  short, ushort
int  |  int, uint
long  |  long, ulong
float, double  |  float, double, decimal
Object  |  object
String  |  string

### 자바 vs C# 3 (식)
자바  |  C#  |  설명
--|--|--
없음  |  ``checked(값)``  |  오버플로우 검사
없음  | ``unchecked(값)``  |  오버플로우 검사 피함

### 자바 vs C# 4 (변수선언, 문)
자바  |  C#  |  설명
--|--|--
``int a;``  |  ``int a;``  |  변수 선언(동일)
``final float PI;``  |  ``const float PI;`` |  상수 선언(값변경 불가)
``System.out.println(..);``  | ``Console.WriteLine(..);``  |  콘솔 출력
```
//자바 switch
switch (selection) {// byte, short, int, char, enum
    case 1: x++; // break가 없으면 다음으로 넘어간다
    case 2: y++; break;
    default: other++;
}

//C# switch
switch (color) { //자료형 제한이 없다.
    case "red": r++; break;// break 꼭 필요
    default: other++; break;
}
```
```
//자바 foreach
foreach (String s : args)
{
    System.out.println(s);
}

//C# foreach
foreach (string s in args)
{
    Console.WriteLine(s);
}
```

### 자바 vs C# 5 (클래스, 개체)
자바  |  C#  |  설명
--|--|--
``class Point3D extends Point `` |  ``class Point3D : Point`` |  클래스 및 인터페이스 상속
``class Watch implements IAlarmClock`` | ``class Watch : IAlarmClock``  |  인터페이스 구현

```
//자바 부모클래스의 생성자 super()
public class BaseClass
{
    int num;

    //생성자 1
    public BaseClass()
    {
        System.out.println("in BaseClass()");
    }

    //생성자 2
    public BaseClass(int i)
    {
        num = i;
        System.out.println("in BaseClass(int i)");
    }

    //메서드 접근제한자기본이 public
    method()
    {
        System.out.println("부모클래스의 메서드 호출!");
    }

    //오버라이드 될 메서드
    overrideMethod()
    {
        System.out.println("오버라이드가 될 메서드 호출!");
    }
}

//DerivedClass 가 BaseClass 를 상속 받음
public class DerivedClass extends BaseClass
{
    //부모클래스의 생성자 1 호출
    public DerivedClass()
    {
        super();
    }

    //부모클래스의 생성자 2 호출
    public DerivedClass(int i)
    {
        super(i);
    }

    //오버라이드
    @override
    overrideMethod()
    {
        System.out.println("오버라이드된 메서드 호출!");
    }
    static void Main()
    {
        DerivedClass md = new DerivedClass();
        DerivedClass md1 = new DerivedClass(1);
        System.out.println(super.num);//부모클래스의 변수 num 호출
        super.method();//부모클래스의 메서드 호출
        overrideMethod();//오버라이드된 메서드 호출
    }
}

//C# 부모클래스의 생성자 base()
public class BaseClass
{
    int num;

    public BaseClass()
    {
        Console.WriteLine("in BaseClass()");
    }

    public BaseClass(int i)
    {
        num = i;
        Console.WriteLine("in BaseClass(int i)");
    }

    //메서드 접근제한자 기본이 private 이므로 public으로 설정한다
    public Method()
    {
        Console.WriteLine("부모클래스의 메서드 호출!");
    }

    //오버라이드 될 메서드
    //C#은 오버라이드할 메서드를 virtual을 붙여서 명시해주어야한다.
    //부모클래스가 override할 메서드를 결정한다!
    protected virtual OverrideMethod()
    {
        Console.WriteLine("오버라이드가 될 메서드 호출!");
    }
}
//DerivedClass 가 BaseClass 를 상속 받음
public class DerivedClass : BaseClass
{
    // This constructor will call BaseClass.BaseClass()
    public DerivedClass() : base()
    {
    }

    // This constructor will call BaseClass.BaseClass(int i)
    public DerivedClass(int i) : base(i)
    {
    }

    //오버라이드
    //C#은 오버라이드할 메서드를 virtual을 붙여서 명시해주어야한다.
    protected override OverrideMethod()
    {
        Console.WriteLine("오버라이드된 메서드 호출!");
    }

    static void Main()
    {
        DerivedClass md = new DerivedClass();
        DerivedClass md1 = new DerivedClass(1);
        Console.WriteLine(base.num);//부모클래스의 변수 num 호출
        base.Method();//부모클래스의 메서드 호출
        OverrideMethod();
    }
}
/*
Output:
in BaseClass()
in BaseClass(int i)
1
부모클래스의 메서드 호출!
오버라이드된 메서드 호출!
*/
```
