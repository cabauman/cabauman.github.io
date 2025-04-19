---
permalink: /about/
title: "About"
---

## About this blog

Welcome to my code journal, where I share insights into my day-to-day development experiences, mostly related to game development. These experiences can range anywhere from bug resolution stories to feature implementations to performance optimizations, etc. Keeping a code journal is a great way to track growth and build a knowledge base, even if it's just in a private Google Doc. By making it available to the public, the hope is that other developers 1) feel inspired and 2) find the information helpful.

## About me

My name is Colt Bauman. I have about 9 years of professional experience, and 16 years overall as a software engineer. I graduated with a Bachelor of Science degree in Game and Simulation Programming in February of 2012, where C++ and C# were the primary languages.

Here's the breakdown of my years of experience in various areas.

| Skill                  | Professional | Hobby | University |
|------------------------|--------------|-------|------------|
| Game Development       | 3            | 10    | 3          |
| Unreal Engine          | 1            | 1     | 1          |
| C++                    | 1            | 1     | 3          |
| Unity and C#           | 7            | 10    | 1          |
| Mobile Development     | 4            | 3     | 0          |
| Backend Engineering    | 2            | 2     | 0          |

<br />

In terms of game development, I'm most passionate about
- 3D vector math
- implementing game mechanics and systems
- low level techniques implemented by game engines

Developer interests and tendencies
- performance optimization
- writing C# source generators
- using Roslyn analyzers to enforce code style consistency
- unit and integration test writing
- dependency injection
- conventional commit messages

### Code Style Preferences

This section is just for fun, so you can get to know some of my coding style taste. These are some of the conventions that I like to establish when starting a new project. But when joining an existing project I don't care which conventions are in use as long as it's consistent.

> **Minimize nested if statements by inverting the condition and returning early.**

```csharp
// NO
if (myClass != null)
{
    if (myClass.Value > 42)
    {
        UpdateValue(myClass.Value);
    }
}

// YES
if (myClass == null)
{
    return;
}
if (myClass.Value <= 42)
{
    return;
}

UpdateValue(myClass.Value);
```

<br />

> Use underscores for private variables.

```csharp
private int _score;
```

<br />

> **Utilize, but don't overuse, the _value object_ pattern to avoid _primitive obsession_.**

**Value object:** a small object that represents a simple entity whose equality is not based on identity: i.e. two value objects are equal when they have the same value, not necessarily being the same object

**Primitive obsession:** when a developer (over)uses primitives (string, int, Guid, decimal, etc) to represent business or domain concepts

For example, consider using the following type instead of a passing around a string that represents a customer ID. Find more details in [this blog post](https://blog.stephencleary.com/2022/10/modern-csharp-techniques-2-value-records.html).

```csharp
public readonly record struct CustomerId(string Value);
```

<br />

> **Method parameters should either all be on one line or each should be on a separate line.**

```csharp
// keep on same line if it doesn't extend too far horizontally
public string JoinName(string first, string last)
{
}

// use separate lines if the signature gets too long
public string JoinName(
    int someRandomNumber,
    string longMethodParameterName1, 
    MySpecialCustomClass longMethodParameterName2)
{
}
```

<br />

> **Use one method invocation per line for method chaining, _with only one level of indentation_.**

```csharp
var firstString = GetListOfStrings()
    .Where(s => true)
    .Where(s => true)
    .Where(s => true)
    .FirstOrDefault();
```

but please don't use deep indentation for alignment 😖

```csharp
var firstString = GetListOfStrings().Where(s => true)
                                    .Where(s => true)
                                    .Where(s => true)
                                    .FirstOrDefault();
```
