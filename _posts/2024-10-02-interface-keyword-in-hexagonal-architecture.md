---
layout: post
title: "Interface keyword in Hexagonal Architecture"
description: "When working in a project with a language that includes the interface keyword I had long discussions about if Hexagon interfaces should be defined with an explicit interface or not, the discussion is a lot of times useless."
date: 2024-10-02
feature_image: images/feature/laptop-code.jpg
tags: [programming, hexagonal-architecture, java]
---

I've had used Hexagonal Architecture in a variety of projects with different languages, and there is a discussion that usually arise when the language contains the keyword `interface`. Some people think that the hexagon interfaces should be explicit, other no, but there is no right or wrong answer and depends on the team common agreements.

In this article I will detail the way I usually implement code in languages that contains `interface` as a keyword. Not better nor worse, just my approximation to the problem :-)

<!--more-->

## Hexagonal Architecture elements

Hexagonal Architecture is also called Ports & Adapters, and usually it is a much better name, implying that the business logic is enclosed by a number of ports and interacts with its surroundings using adapters.

{% include image_caption.html imageurl="/images/hexagonal-architecture-elements.png" title="Elements of Hexagonal Architecture basic diagram" caption="Elements of Hexagonal Architecture basic diagram" %}

There are a number of elements, but for this article we will focus on the ports:
* **Driving ports** are the entry point into the application from an external system or actor.
* **Driven ports** are the points used to interact with external systems to complete an operation by the application, it could be usually a DB, a REST API, etc.

In a few words, when I implement a system with Hexagonal Architecture in Java, I use explicit interfaces for the driven ports, but not for the driving ports. And now we will go deeper into the why. 

## My usual way of working

Let's take a basic example, a system that must be able to get a list of ingredients and introduce new ones. If using Hexagonal Architecture I would usually draw a diagram like the following one.

{% include image_caption.html imageurl="/images/hexagonal-architecture-ingredients.png" title="Ingredients API with Hexagonal Architecture" caption="Ingredients API with Hexagonal Architecture" %}

There is a driving port `ForManagingIngredients` and a driven port `ForPersistingIngredients`, the first one will be implicit and the second on will be explicit. So `IngredientsCatalog` will be the component to use by the driving adapter.

```java
public class IngredientsCatalog {
    private ForPersistingIngredients ingredientsRepository;

    public IngredientsCatalog(ForPersistingIngredients ingredientsRepository) {
        this.ingredientsRepository = ingredientsRepository;
    }

    public List<Ingredient> getIngredients(int page, int size) {
        return ingredientsRepository.getIngredients(page, size);
    }

    public Ingredient addIngredient(IngredientCreationCommand newIngredient) {
        IngredientsCatalog.validateIngredient(newIngredient);

        if (ingredientsRepository.doesExist(newIngredient.name())) {
            var errorMessage = MessageFormat.format("Ingredient {0} already exists", newIngredient.name());
            throw new AlreadyExistingIngredientException(errorMessage);
        }

        return ingredientsRepository.addIngredient(newIngredient);
    }

    // ...
    
}
```

As you can see there is no reference to an interface using the `implements` keyword. One question could be "Why don't you define the interface?", the answer is because it is already defined. `ForManagingIngredients` already exists in an implicit way, and I decide not to define because there are barely no reasons to have a second implementation. `IngredientsCatalog` is the only implementation, my way to do TDD, outside-in, don't get any advantage from having an explicit interface, so another reason to skip it.

In other languages it wouldn't be a discussion since the explicit interface does not exist, but it is something that is discussed in Java or Type Script projects.

At this point you could think that in the driven ports I do the same, but actually, I don't. For the driven adapters I always use an explicit interface. As you can see in the code there is a reference to `IngredientsRepository`.

```java
public interface ForPersistingIngredients {
    List<Ingredient> getIngredients(int page, int size);
    Ingredient addIngredient(IngredientCreationCommand newIngredient);
    boolean doesExist(String ingredientName);
}
```

One of the reasons I do this, is because while I am doing the TDD cycle I am just thinking about the methods I need, so I define them with the `interface`, I will worry about implementation and details later. Not a very impressive reason, I know.

Another one is that at this point I have a "folder" with `IngredientsCatalog` and `IngredientsRepository` creating a single module that has value by itself, and it is independent of frameworks and technology, it is important to keep business code isolated from spurious details.

Finally, I've found by experience that having mocked implementations could make integration tests simpler and faster. And these mocked implementations could work well for local tests or environments different from production. Nowadays larger tests using [TestContainers](https://testcontainers.com/) are simple enough, and run quite fast, but I am talking about something closer to unit tests here.

For `IngredientsRepository` you could have something as simple as:

```java
public class InMemoryIngredientsRepository implements ForPersistingIngredients {
    private List<Ingredient> internalIngredientsDictionary = new ArrayList<>();

    public InMemoryIngredientsRepository() {
        internalIngredientsDictionary.add(new Ingredient("23f3423f-3c38-48ec-afd9-0aceea05aa4d", "Lemon", List.of("JAN", "FEB", "MAR", "APR", "MAY")));
        internalIngredientsDictionary.add(new Ingredient("6ec213a1-9e1d-4a73-ba5f-dfc621102af9", "Onion", List.of("APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT")));
        internalIngredientsDictionary.add(new Ingredient("17edc0d1-5525-42d9-8d75-84c94996cd84", "Watermelon", List.of("JUN", "JUL", "AUG")));
    }

    @Override
    public List<Ingredient> getIngredients(int page, int size) {
        return internalIngredientsDictionary.stream()
                .sorted(Comparator.comparing(Ingredient::name))
                .skip((page - 1) * size)
                .limit(size)
                .collect(Collectors.toList());

    }

    @Override
    public Ingredient addIngredient(IngredientCreationCommand newIngredient) {
        var ingredient = new Ingredient(UUID.randomUUID().toString(), newIngredient.name(), newIngredient.seasonality());
        internalIngredientsDictionary.add(ingredient);

        return ingredient;
    }

    @Override
    public boolean doesExist(String ingredientName) {
        var matchingIngredients = internalIngredientsDictionary.stream().filter(ingredient -> ingredient.name().equals(ingredientName)).toList();
        return matchingIngredients.size() > 0;
    }
}
```

But there are other cases. Imaging that you use a third party service that you cannot (or you don't want) invoke in local executions, changing the injected object during the bootstraping by a mock could simplify things a lot. This allows for faster, but safe enough, developments where all business code is actually tested.

## There is always an interface

The important point in all this discussion is that the interfaces are always there, no matter if you define the explicit ones or not. Having an explicit one would make it easier to detect if the interface is being changed in an undesired way, but in some cases it is just boilerplate that adds nearly no value. Joining your team and deciding the way you want to work is the good way to go here, but at least make it an informed decision.

## Misc and references

* Photo from <a href="https://unsplash.com/es/@altumcode?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">AltumCode</a> in <a href="https://unsplash.com/es/fotos/encendio-la-computadora-portatil-dC6Pb2JdAqs?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
* Some reference code at [My Recipes Github repository](https://github.com/ydarias/my-recipes)
