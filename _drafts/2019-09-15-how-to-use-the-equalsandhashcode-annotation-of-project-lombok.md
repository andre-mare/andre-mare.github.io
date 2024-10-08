---
layout: post
title: "How to Use the @EqualsAndHashCode Annotation of Project Lombok"
date: 2019-09-15 00:00:00 +0200
tags: java lombok equalsandhashcode
categories: [Lombok]
author: "andre_mare"
post_image: "/assets/img/my_images/feature-images/feature-image-lombok.png"
---

This post will focus on how to make use of the @EqualsAndHashCode annotation of Project Lombok. The Lombok Project is a java library that helps a developer generate boilerplate code. By simply adding the Lombok library to your IDE and build path the Lombok library will auto-generate the Java bytecode, as per the annotations, into the .class files.

The @EqualsAndHashCode annoation is added to a class and Lombok will generate the implementation of the equals and hashCode methods.


## Article Series
This article forms part of a multi-part series on how to use the Project Lombok to generate boilerplate code in java projects.

* [How to Use the @AllArgsConstructor Annotation of Project Lombok][Article1]
* [How to Use the @Builder Annotation of Project Lombok][Article2]
* [How to Use the @CleanUp Annotation of Project Lombok][Article3]
* [How to Use the @Data Annotation of Project Lombok][Article4]
* [How to Use the @EqualsAndHashCode Annotation of Project Lombok][Article5]
* [How to Use the @Getter and @Setter Annotations of Project Lombok][Article6]


#### Code Example
The code example can be downloaded from Github from the button below.

<a href="https://github.com/Code2Bits/Java-Library-Examples/tree/master/Lombok/LombokExamples/src/main/java/com/code2bits/lombok/example/equals" class="btn">Download Code</a>

#### Define Maven Dependencies
The following dependencies should be included in the pom.xml file.
```xml
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
  <version>1.18.8</version>
  <scope>provided</scope>
</dependency>
```

#### Example: @EqualsAndHashCode
The @EqualsAndHashCode annoation is added to a class and Lombok will generate the implementation of the equals and hashCode methods.

**Original Class**
```java
@EqualsAndHashCode
public class EqualsAndHashCodeExample01 {

    private long id;
    private String firstName;
    private String lastName;

    public EqualsAndHashCodeExample01(long id, String firstName, String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public static void main(String[] args) {
        EqualsAndHashCodeExample01 example01 = new EqualsAndHashCodeExample01(1, "Joe", "Soap");
        EqualsAndHashCodeExample01 example02 = new EqualsAndHashCodeExample01(1, "Joe", "Soap");

        System.out.println("Example 1 - HashCode: " + example01.hashCode());
        System.out.println("Example 2 - HashCode: " + example02.hashCode());
        System.out.println("Example 1 Equals Example 2: " + example01.equals(example02));
    }
}
```

To truly appreciate the magic of the Lombok library, you should compile the EqualsAndHashCodeExample01 class by making use of maven to build your project. As part of the compile process, Lombok will generate the boilerplate code depending on the type of annotation you used. To see the boilerplate code, you should decompile EqualsAndHashCodeExample01.class file. An easy way to do this is to make use of the following URL:

<p>http://www.javadecompilers.com</p>

**Decompiled Class**
```java
public class EqualsAndHashCodeExample01
{
    private long id;
    private String firstName;
    private String lastName;
    
    public EqualsAndHashCodeExample01(final long id, final String firstName, final String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }
    
    public static void main(final String[] args) {
        final EqualsAndHashCodeExample01 example01 = new EqualsAndHashCodeExample01(1L, "Joe", "Soap");
        final EqualsAndHashCodeExample01 example2 = new EqualsAndHashCodeExample01(1L, "Joe", "Soap");
        System.out.println("Example 1 - HashCode: " + example01.hashCode());
        System.out.println("Example 2 - HashCode: " + example2.hashCode());
        System.out.println("Example 1 Equals Example 2: " + example01.equals(example2));
    }
    
    @Override
    public boolean equals(final Object o) {
        if (o == this) {
            return true;
        }
        if (!(o instanceof EqualsAndHashCodeExample01)) {
            return false;
        }
        final EqualsAndHashCodeExample01 other = (EqualsAndHashCodeExample01)o;
        if (!other.canEqual(this)) {
            return false;
        }
        if (this.id != other.id) {
            return false;
        }
        final Object this$firstName = this.firstName;
        final Object other$firstName = other.firstName;
        Label_0079: {
            if (this$firstName == null) {
                if (other$firstName == null) {
                    break Label_0079;
                }
            }
            else if (this$firstName.equals(other$firstName)) {
                break Label_0079;
            }
            return false;
        }
        final Object this$lastName = this.lastName;
        final Object other$lastName = other.lastName;
        if (this$lastName == null) {
            if (other$lastName == null) {
                return true;
            }
        }
        else if (this$lastName.equals(other$lastName)) {
            return true;
        }
        return false;
    }
    
    protected boolean canEqual(final Object other) {
        return other instanceof EqualsAndHashCodeExample01;
    }
    
    @Override
    public int hashCode() {
        final int PRIME = 59;
        int result = 1;
        final long $id = this.id;
        result = result * 59 + (int)($id >>> 32 ^ $id);
        final Object $firstName = this.firstName;
        result = result * 59 + (($firstName == null) ? 43 : $firstName.hashCode());
        final Object $lastName = this.lastName;
        result = result * 59 + (($lastName == null) ? 43 : $lastName.hashCode());
        return result;
    }
}
```

#### Summary
Congratulations !!! You have successfully used the @EqualsAndHashCode annotation of Project Lombok. Please look out for more examples on how to make use of Project Lombok to simplify your Java coding experience.

[Lombok]:https://projectlombok.org/download
[Install_Maven]:{{site.baseurl}}/how-to-install-maven-on-macos-using-homebrew/
[Install_Java]:{{site.baseurl}}/how-to-install-java-on-macos-using-homebrew/
[Install_STS]:/how-to-install-sts-on-macos-using-homebrew/
[Install_Eclipse]:/how-to-install-eclipse-on-macos-using-homebrew/
[Install_IntelliJ]:/how-to-install-intellij-idea-community-edition-on-macos-using-homebrew/

[Article1]:/how-to-use-the-allargsconstructor-annotation-of-project-lombok/
[Article2]:/how-to-use-the-builder-annotation-of-project-lombok/
[Article3]:/how-to-use-the-cleanup-annotation-of-project-lombok/
[Article4]:/how-to-use-the-data-annotation-of-project-lombok/
[Article5]:/how-to-use-the-equalsandhashcode-annotation-of-project-lombok/
[Article6]:/how-to-use-the-getter-and-setter-annotation-of-project-lombok/