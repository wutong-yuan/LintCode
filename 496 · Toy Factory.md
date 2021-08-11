# 496 · Toy Factory

**# 496 · Toy Factory**
**
**
/**
 * Your object will be instantiated and called as such:
 * ToyFactory tf = new ToyFactory();
 * Toy toy = tf.getToy(type);
 * toy.talk();
 */
interface Toy {
    void talk();
}

class Dog implements Toy {
    // Write your code here
    @Override
    public void talk() {
        System.out.print("Wow");
    }
}

class Cat implements Toy {
    // Write your code here
    @Override
    public void talk() {
        System.out.print("Meow");
    }
}

public class ToyFactory {
    /**
     * @param type a string
     * @return Get object of the type
     */

    public Toy getToy(String type) {
        if (type == null) return null;
        // Write your code here
        if (type.equalsIgnoreCase("Dog")) {
            return new Dog();
        } else if (type.equalsIgnoreCase("Cat")) {
            return new Cat();
        }
        return null;
    }
}
