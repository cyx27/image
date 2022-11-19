# 向下转型时使用instanceof判断是否是某类的实例（保证安全）

```java
public class Shape {
    void f(){
        System.out.println("父类");
    }
}

public class Circle extends Shape{
    @Override
    void f() {
        System.out.println("circle");
    }
}

public class Rectangle extends Shape{
    @Override
    void f() {
        System.out.println("rectangle");
    }
}

public class test {
    public static void main(String[] args) {
        ArrayList<Shape> arrayList = new ArrayList<>();
        arrayList.add(new Circle());
        arrayList.add(new Rectangle());
        
        for (Shape shape : arrayList) {
            if (shape instanceof Circle) { // 向下转型
                Circle circle = (Circle) shape;
                circle.f();
            } else if (shape instanceof Rectangle) {
                Rectangle rectangle = (Rectangle) shape;
                rectangle.f();
            }
        }
    }
}
```