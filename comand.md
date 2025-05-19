
# 🧠 Command Pattern in Java

The **Command Pattern** is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. It decouples the sender and the receiver of the request.

---

## 🔧 Problem

You want to parameterize objects with operations, delay execution, queue commands, or support undo/redo. Hardcoding actions into buttons or UI elements tightly couples the logic and limits flexibility.

---

## 📦 Structure

| Role             | Responsibility |
|------------------|----------------|
| **Command**       | Declares `execute()` method |
| **ConcreteCommand** | Implements `Command`, delegates action to the Receiver |
| **Receiver**      | Knows how to perform the work |
| **Invoker**       | Asks the command to carry out the request |
| **Client**        | Creates commands and sets up relationships between objects |

---

## 🧱 Code Example

### ✅ Receiver

```java
public class Light {
    public void turnOn() {
        System.out.println("Light is ON");
    }
    public void turnOff() {
        System.out.println("Light is OFF");
    }
}
````

### ✅ Command Interface

```java
public interface Command {
    void execute();
}
```

### ✅ Concrete Commands

```java
public class LightOnCommand implements Command {
    private Light light;

    public LightOnCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }
}

public class LightOffCommand implements Command {
    private Light light;

    public LightOffCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOff();
    }
}
```

### ✅ Invoker

```java
public class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}
```

### ✅ Client Code

```java
public class Main {
    public static void main(String[] args) {
        Light light = new Light();

        Command lightsOn = new LightOnCommand(light);
        Command lightsOff = new LightOffCommand(light);

        RemoteControl remote = new RemoteControl();

        remote.setCommand(lightsOn);
        remote.pressButton(); // Output: Light is ON

        remote.setCommand(lightsOff);
        remote.pressButton(); // Output: Light is OFF
    }
}
```

---

## ✅ Benefits

* Decouples the sender and receiver
* Easy to add new commands without changing existing code
* Supports logging, queuing, undo/redo
* Cleaner, testable design

---

## ❌ Drawbacks

* Requires more classes (boilerplate)
* Slight complexity overhead

---

## 🧪 Extensions

* Implement `undo()` method for reversible actions
* Create a `MacroCommand` to run multiple commands at once
* Store commands in history for undo functionality

---

## 📚 Related Patterns

* **Strategy** – Encapsulates algorithms; Command encapsulates actions
* **Memento** – Often used with Command to support undo
* **Observer** – Can notify receivers about command execution

---

> This is a simplified example. Real-world usage often involves more dynamic and flexible command handling (e.g., command queues, undo stacks, or serialized commands).

```
