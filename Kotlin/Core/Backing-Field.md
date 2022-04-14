:question: What is Kotlin ***Backing Field***?

:white_check_mark: A Backing Field is just a field that will be generated automatically for a property in a class only if it uses the default implementation of at least one of the accessors(getter/setter).

:question: Can you give me an example?

🐝 Consider this Kotlin class:

```kotlin
class DummyClass {
    var size = 0;
    var isEmpty
        get() = size == 0
        set(value) {
            size = size * 2
        }
}
```

We can see that it has 2 properties i.e - size(with default accessors) and isEmpty(with custom accessors). But it has only 1 field i.e. size. To understand that it has only 1 field, let us see the Java equivalent of this class:

```java
   public final class DummyClass {
   private int size;

   public final int getSize() {
      return this.size;
   }

   public final void setSize(int var1) {
      this.size = var1;
   }

   public final boolean isEmpty() {
      return this.size == 0;
   }

   public final void setEmpty(boolean value) {
      this.size *= 2;
   }
}
```

We can see the java class has only getter and setter functions for isEmpty, and there is no field declared for it. Similarly in Kotlin, there is no backing field for property isEmpty, since the property doesn't depend on that field at all. Thus no backing field.
Now let us remove the custom getter and setter of isEmpty property.

```kotlin
class DummyClass {
    var size = 0;
    var isEmpty = false
}
```

And the Java equivalent of the above class is

```java
public final class DummyClass {
   private int size;
   private boolean isEmpty;

   public final int getSize() {
      return this.size;
   }

   public final void setSize(int var1) {
      this.size = var1;
   }

   public final boolean isEmpty() {
      return this.isEmpty;
   }

   public final void setEmpty(boolean var1) {
      this.isEmpty = var1;
   }
}
```
Here we see both the fields size and isEmpty. isEmpty is a backing field because the getter and setter for isEmpty property depend upon it.



:question: Can you explain more?

:white_check_mark: https://www.baeldung.com/kotlin/backing-fields
