public abstract class Shape {
    protected double radius;
    protected double height;

    public Shape(double radius, double height) {
        this.radius = radius;
        this.height = height;
    }

    public abstract double surfaceArea();

    public abstract double volume();

    @Override
    public String toString() {
        return "Radius: " + radius + ", Height: " + height + ", Surface Area: " + surfaceArea() + ", Volume: " + volume();
    }
}
public class Sphere extends Shape {
    public Sphere(double radius) {
        super(radius, 0.0); // Height is not used for spheres
    }

    @Override
    public double surfaceArea() {
        return 4 * Math.PI * radius * radius;
    }

    @Override
    public double volume() {
        return (4.0 / 3.0) * Math.PI * Math.pow(radius, 3);
    }

    @Override
    public String toString() {
        return "Sphere - " + super.toString();
    }
}
public class Cylinder extends Shape {
    public Cylinder(double radius, double height) {
        super(radius, height);
    }

    @Override
    public double surfaceArea() {
        return 2 * Math.PI * radius * (radius + height);
    }

    @Override
    public double volume() {
        return Math.PI * Math.pow(radius, 2) * height;
    }

    @Override
    public String toString() {
        return "Cylinder - " + super.toString();
    }
}
public class Cone extends Shape {
    public Cone(double radius, double height) {
        super(radius, height);
    }

    @Override
    public double surfaceArea() {
        double slantHeight = Math.sqrt(Math.pow(radius, 2) + Math.pow(height, 2));
        return Math.PI * radius * (radius + slantHeight);
    }

    @Override
    public double volume() {
        return (1.0 / 3.0) * Math.PI * Math.pow(radius, 2) * height;
    }

    @Override
    public String toString() {
        return "Cone - " + super.toString();
    }
}
public class ShapeArray {
    public static void main(String[] args) {
        Shape[] shapeArray = new Shape[3];

        shapeArray[0] = new Sphere(3.0);
        shapeArray[1] = new Cylinder(2.0, 5.0);
        shapeArray[2] = new Cone(4.0, 6.0);

        for (Shape shape : shapeArray) {
            System.out.println(shape.toString());
        }
    }
}
