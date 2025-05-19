
# 🧠 Command Pattern in Java

Das **Command Pattern** (Befehlsmuster) ist ein Verhaltensentwurfsmuster, das eine Anforderung in ein eigenständiges Objekt kapselt. Dadurch wird der Sender einer Anforderung vom Empfänger entkoppelt.

---

## 🔧 Problem

Du möchtest Objekte mit Operationen parametrieren, Ausführungen verzögern, Befehle in eine Warteschlange stellen oder Undo/Redo unterstützen. Wenn die Aktionen direkt im UI (z. B. Button) kodiert sind, wird die Flexibilität eingeschränkt.

---

## 📦 Struktur

| Rolle              | Verantwortung |
|--------------------|----------------|
| **Command**         | Deklariert die Methode `execute()` |
| **ConcreteCommand** | Implementiert `Command`, delegiert die Aktion an den Receiver |
| **Receiver**        | Kennt die konkreten Aktionen (z. B. Licht ein-/ausschalten) |
| **Invoker**         | Startet die Ausführung des Befehls |
| **Client**          | Erstellt Befehle und konfiguriert das System |

---

## 🧱 Beispiel in Java

### ✅ Empfänger (Receiver)

```java
public class Light {
    public void turnOn() {
        System.out.println("Licht ist AN");
    }
    public void turnOff() {
        System.out.println("Licht ist AUS");
    }
}
````

### ✅ Befehl-Interface (Command)

```java
public interface Command {
    void execute();
}
```

### ✅ Konkrete Befehle (ConcreteCommand)

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

### ✅ Auslöser (Invoker)

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

### ✅ Anwendung (Client)

```java
public class Main {
    public static void main(String[] args) {
        Light light = new Light();

        Command lightsOn = new LightOnCommand(light);
        Command lightsOff = new LightOffCommand(light);

        RemoteControl remote = new RemoteControl();

        remote.setCommand(lightsOn);
        remote.pressButton(); // Ausgabe: Licht ist AN

        remote.setCommand(lightsOff);
        remote.pressButton(); // Ausgabe: Licht ist AUS
    }
}
```

---

## ✅ Vorteile

* Entkopplung von Sender und Empfänger
* Neue Befehle können leicht hinzugefügt werden
* Unterstützt Logging, Warteschlangen, Undo/Redo
* Sauberes, testbares Design

---

## ❌ Nachteile

* Mehr Klassen (Overhead)
* Etwas komplexere Architektur

---

## 🧪 Erweiterungen

* `undo()`-Methode für Aktionen mit Rückgängig-Funktion
* `MacroCommand`, um mehrere Befehle auf einmal auszuführen
* Befehle in einer History speichern

---

## 📚 Verwandte Muster

* **Strategy** – Kapselt Algorithmen; Command kapselt Aktionen
* **Memento** – Oft mit Command für Undo-Funktionalität kombiniert
* **Observer** – Zum Reagieren auf Befehlsausführungen geeignet

---

> Dies ist ein vereinfachtes Beispiel. In der Praxis kann das Muster mit Befehlswarteschlangen, History oder Netzwerkbefehlen erweitert werden.

```

