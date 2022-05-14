# Design Pattern

* Adaptor pattern
* Delegation Pattern
* Builder Pattern
* Factory Pattern
* Proxy Pattern




<br><br><br>

## 어댑터 패턴

## 위임 패턴 (Delegation pattern)

## 빌더 패턴

``` java
// example
public class Computer {

    private final String ram;
    private final String cpu;
    private final String hdd;

    public Computer(ComputerBuilder builder) {
        this.ram = builder.ram;
        this.cpu = builder.cpu;
        this.hdd = builder.hdd;
    }

    public String getRam() {
        return ram;
    }

    public String getCpu() {
        return cpu;
    }

    public String getHdd() {
        return hdd;
    }

    public static class ComputerBuilder {
        private String ram;
        private String cpu;
        private String hdd;

        public ComputerBuilder() {
        }

        public ComputerBuilder ram(String ram) {
            this.ram = ram;
            return this;
        }

        public ComputerBuilder cpu(String cpu) {
            this.cpu = cpu;
            return this;
        }

        public ComputerBuilder hdd(String hdd) {
            this.hdd = hdd;
            return this;
        }

        public Computer build() {
            return new Computer(this);
        }
    }
}


public class ComputerApp {
    public static void main(String[] args) {

        Computer computer = new Computer.ComputerBuilder()
                .cpu("i5")
                .hdd("R550")
                .ram("32G")
                .build();

        String cpu = computer.getCpu();
        System.out.println("cpu = " + cpu);

        String hdd = computer.getHdd();
        System.out.println("hdd = " + hdd);

        String ram = computer.getRam();
        System.out.println("ram = " + ram);
    }
}



```



## 팩토리 패턴

## 프록시 패턴







<br><br><br>
<br><br><br>
<br><br><br>

### [참고] <br>
  * Builder pattern <br>
  *-* java Builder pattern [article] - https://blogs.oracle.com/javamagazine/post/exploring-joshua-blochs-builder-design-pattern-in-java <br>