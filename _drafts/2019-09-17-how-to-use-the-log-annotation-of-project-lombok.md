---
layout: post
title: "How to Use the @Log Annotation of Project Lombok"
date: 2019-09-17 00:00:00 +0200
tags: java lombok log
categories: [Lombok]
author: "andre_mare"
post_image: "/assets/img/my_images/feature-images/feature-image-lombok.png"
---

This post will focus on how to make use of the @log annotation and other variants of Project Lombok. The Lombok Project is a java library that helps a developer generate boilerplate code. By simply adding the Lombok library to your IDE and build path the Lombok library will auto-generate the Java bytecode, as per the annotations, into the .class files.

The @Log annotation is added to the top of a class which and Lombok will generate the logger field. The logger is named log and the field's type depends on which logger you have selected.

## Article Series
This article forms part of a multi-part series on how to use the Project Lombok to generate boilerplate code in java projects.

* [How to Use the @AllArgsConstructor Annotation of Project Lombok][Article1]
* [How to Use the @Builder Annotation of Project Lombok][Article2]
* [How to Use the @CleanUp Annotation of Project Lombok][Article3]
* [How to Use the @Data Annotation of Project Lombok][Article4]
* [How to Use the @EqualsAndHashCode Annotation of Project Lombok][Article5]
* [How to Use the @Getter and @Setter Annotations of Project Lombok][Article6]


#### Java Mutators and Accessors (Getters & Setters)
In Java, a mutator method is a method used to control changes to a variable within a Java class. They are also widely known as setter methods. Often a setter is accompanied by a getter (also known as an accessor), which returns the value of the private member variable.

There are many opinions about the use of Getter and Setter methods, and when to use them correctly, but this will not be discussed in this post. Let’s assume that you have correctly applied Object Oriented principles to the design of your Java class and require the getter and setter methods.

If a Java class contains a large number of member attributes, it will contain a large number of boilerplate code like the getter and setter methods, and hence the use of the Lombok library makes it much easier to generate the code. This means fewer errors can occur when writing the code yourself, and the class is easier to read and understand.

Java Access Modifiers specifies the scope (accessibility) of member attributes, methods, constructors and classes. There are 4 types of access modifiers in Java namely, private, default, protected and public.

<ul>
<li>The <strong>public</strong> access modifier specifies that the member and/or method can be accessed from anywhere.</li>
<li>The <strong>protected</strong> access modifier specifies that the member and/or method  can only be accessed within its own package (as with package-private) and, in addition, by a subclass of its class in another package.</li>
<li>The <strong>default</strong> access modifier (package-private or no modifier specified) specifies that the member and/or method  is only visible within its own package.</li>
<li>The <strong>private</strong> access modifier specifies that the member and/or method can only be accessed in its own class.</li>
</ul>

#### Code Example
The code example can be downloaded from Github from the button below.

<a href="https://github.com/Code2Bits/Java-Library-Examples/tree/master/Lombok/LombokExamples/src/main/java/com/code2bits/lombok/example/gettersetter" class="btn">Download Code</a>

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

#### Example 1: @Getter and @Setter on Class
This example will focus on how to make use of the @Getter and @Setter annotations on the top off a class to generate the mutator and accessor methods of a class. This is similar as if you annotate all the non-static fields in that class with the annotations.

**Original Class**
```java
@Getter
@Setter
public class GetterSetterExample01 {
    private long id;
    private String firstName;
    private String lastName;
    private String gender;
    private Date birthDate;
    private String contactEmail;
    private boolean isFirstYear;
}
```

To truly appreciate the magic of the Lombok library, you should compile the GetterSetterExample01 class by making use of maven to build your project. As part of the compile process, Lombok will generate the boilerplate code depending on the type of annotation you used. To see the boilerplate code, you should decompile GetterSetterExample01.class file. An easy way to do this is to make use of the following URL:

<p>http://www.javadecompilers.com</p>

**Decompiled Class**
```java
public class GetterSetterExample01
{
    private long id;
    private String firstName;
    private String lastName;
    private String gender;
    private Date birthDate;
    private String contactEmail;
    private boolean isFirstYear;
    
    public long getId() {
        return this.id;
    }
    
    public String getFirstName() {
        return this.firstName;
    }
    
    public String getLastName() {
        return this.lastName;
    }
    
    public String getGender() {
        return this.gender;
    }
    
    public Date getBirthDate() {
        return this.birthDate;
    }
    
    public String getContactEmail() {
        return this.contactEmail;
    }
    
    public boolean isFirstYear() {
        return this.isFirstYear;
    }
    
    public void setId(final long id) {
        this.id = id;
    }
    
    public void setFirstName(final String firstName) {
        this.firstName = firstName;
    }
    
    public void setLastName(final String lastName) {
        this.lastName = lastName;
    }
    
    public void setGender(final String gender) {
        this.gender = gender;
    }
    
    public void setBirthDate(final Date birthDate) {
        this.birthDate = birthDate;
    }
    
    public void setContactEmail(final String contactEmail) {
        this.contactEmail = contactEmail;
    }
    
    public void setFirstYear(final boolean isFirstYear) {
        this.isFirstYear = isFirstYear;
    }
}
```

#### Example 2: @Getter and @Setter on member attributes
This example will focus on how to make use of the @Getter and @Setter annotations on top off the member attributes of a class to generate the mutator and accessor methods for those fields. This example will also describe how to define Access Levels for the mutator and accessor methods.

**Original Class**
```java
public class GetterSetterExample02 {

    @Getter @Setter(AccessLevel.PRIVATE)
    private long id;

    @Getter @Setter(AccessLevel.PROTECTED)
    private String firstName;

    @Getter @Setter(AccessLevel.PUBLIC)
    private String lastName;

    @Getter @Setter(AccessLevel.PACKAGE)
    private String gender;

    @Getter @Setter(AccessLevel.MODULE)
    private Date birthDate;

    @Getter @Setter(AccessLevel.NONE)
    private String contactEmail;

    @Getter @Setter
    private boolean isFirstYear;
}
```

To see the boilerplate code, you should decompile GetterSetterExample02.class file. An easy way to do this is to make use of the following URL:

<p>http://www.javadecompilers.com</p>

**Decompiled Class**
```java
public class GetterSetterExample02
{
    private long id;
    private String firstName;
    private String lastName;
    private String gender;
    private Date birthDate;
    private String contactEmail;
    private boolean isFirstYear;
    
    public long getId() {
        return this.id;
    }
    
    private void setId(final long id) {
        this.id = id;
    }
    
    public String getFirstName() {
        return this.firstName;
    }
    
    protected void setFirstName(final String firstName) {
        this.firstName = firstName;
    }
    
    public String getLastName() {
        return this.lastName;
    }
    
    public void setLastName(final String lastName) {
        this.lastName = lastName;
    }
    
    public String getGender() {
        return this.gender;
    }
    
    void setGender(final String gender) {
        this.gender = gender;
    }
    
    public Date getBirthDate() {
        return this.birthDate;
    }
    
    void setBirthDate(final Date birthDate) {
        this.birthDate = birthDate;
    }
    
    public String getContactEmail() {
        return this.contactEmail;
    }
    
    public boolean isFirstYear() {
        return this.isFirstYear;
    }
    
    public void setFirstYear(final boolean isFirstYear) {
        this.isFirstYear = isFirstYear;
    }
}
```

So based on the example, the following are the reasons why lombok generated the methods with different java access modifiers:

<ul>
<li><strong>Member Attribute: id</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is private because the AccessLevel was set to PRIVATE.</li>

<li><strong>Member Attribute: firstName</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is protected because the AccessLevel was set to PROTECTED.</li>

<li><strong>Member Attribute: lastName</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is public because the AccessLevel was set to PUBLIC.</li>

<li><strong>Member Attribute: gender</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is "default" because the AccessLevel was set to PACKAGE.</li>

<li><strong>Member Attribute: birthDate</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is "default" because the AccessLevel was set to MODULE.</li>

<li><strong>Member Attribute: contactEmail</strong> - The accessor method is public because the AccessLevel was not specified. The mutator method is not generated because the AccessLevel was set to NONE.</li>

<li><strong>Member Attribute: isFirstYear</strong> - The accessor method is public because the AccessLevel was not specified. The accessor method is public because the AccessLevel was not specified.</li>
</ul>


#### Summary
Congratulations !!! You have successfully used the @Getter and @Setter annotations of Project Lombok. Please look out for more examples on how to make use of Project Lombok to simplify your Java coding experience.

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
[Article7]:/how-to-use-the-log-annotation-of-project-lombok/