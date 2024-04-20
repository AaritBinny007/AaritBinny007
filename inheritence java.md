class Employee {
    String name;

    Employee(String x) {
        name = x;
    }

    void display() {
        System.out.println("Name: " + name); // Change 'x' to 'name'
    }
}

class Manager extends Employee {
    int year;

    Manager(String x, int t) {
        super(x);
        year = t;
    }

    void display() {
        super.display();
        System.out.println("Year: " + year); // Change 't' to 'year'
    }
}

class SeniorManager extends Manager {
    int salary;

    SeniorManager(String n, int t, int s) {
        super(n, t);
        salary = s;
    }

    void display() {
        super.display();
        System.out.println("Salary: " + salary);
    }
}

class JuniorManager extends Manager {
    int salary;

    JuniorManager(String n, int t, int s) {
        super(n, t);
        salary = s;
    }

    void display() {
        super.display();
        System.out.println("Salary: " + salary);
    }
}

class Developer extends Employee {
    int year;

    Developer(String n, int y) {
        super(n);
        year = y;
    }

    void display() {
        super.display();
        System.out.println("Year: " + year);
    }
}

class SeniorDeveloper extends Developer {
    int salary;

    SeniorDeveloper(String n, int y, int s) {
        super(n, y);
        salary = s;
    }

    void display() {
        super.display();
        System.out.println("Salary: " + salary);
    }
}

class JuniorDeveloper extends Developer {
    int salary;

    JuniorDeveloper(String n, int y, int s) {
        super(n, y);
        salary = s;
    }

    void display() {
        super.display();
        System.out.println("Salary: " + salary);
    }
}

class Intern extends Employee {
    int salary;

    Intern(String n, int y) {
        super(n);
        salary = y;
    }

    void display() {
        super.display();
        System.out.println("Salary: " + salary);
    }
}

public class Employees {
    public static void main(String[] arg) {
        Employee e1;
        SeniorManager e2 = new SeniorManager("Christopher", 18, 240000);
        JuniorManager e3 = new JuniorManager("Adhin", 8, 180000);
        SeniorDeveloper e4 = new SeniorDeveloper("Aarit", 9, 100000);
        JuniorDeveloper e5 = new JuniorDeveloper("Bijay", 3, 55000);
        Intern e6 = new Intern("Bosco", 4000);

        e1 = e2;
        e1.display();
        e1 = e3;
        e1.display();
        e1 = e4;
        e1.display();
        e1 = e5;
        e1.display();
        e1 = e6;
        e1.display();
    }
}
