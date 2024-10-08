---
layout: post
title: "Hexagonal Architecture: Too much boilerplate?"
description: "Depending on your style, it is possible that you have some boilerplate in your code to adapt inputs and outputs, but is that really bad?"
date: 2024-10-08
feature_image: images/feature/designer.jpg
tags: [programming, software-architecture, hexagonal-architecture]
---

I am currently working on a pet project to refresh Java tech-stack knowledge, and I got to this class.

```java
public class RecipesController {
    private RecipesCatalog recipesCatalog;

    public RecipesController(RecipesCatalog recipesCatalog) {
        this.recipesCatalog = recipesCatalog;
    }

    public List<RecipeResponse> getRecipes(
            @RequestParam(defaultValue = "1") int page,
            @RequestParam(defaultValue = "10") int size) {
        var recipes = recipesCatalog.getRecipes(page, size);
        return recipes.stream().map(RecipesController::asRecipeResponse).toList();
    }

    private static RecipeResponse asRecipeResponse(Recipe recipe) {
        return new RecipeResponse(recipe.id(), recipe.name(), recipe.recap());
    }
}
```

It reminded me of the main complaint people tell me about Hexagonal Architecture, the need for boilerplate. Do you see the `RecipesController::asRecipeResponse` reference? Why not returning just a list of `Recipe`? Why using mappers all the time? Well, there are a few reasons to do that.

<!--more-->

First thing first, you could simply return a list of `Recipe` and the hexagon is not affected at all, but let's think about some different scenarios.

## Independent models

Putting it simple, **it is very flexible to keep the adapter and business models separated**, so you can make changes to them independently and then map to each other. But there are more esoteric cases, specially if the business is growing over years, and you have to offer other integration points.

{% include image_caption.html imageurl="/images/hexagonal/hexagonal-multiple-adapters.png" title="Multiple adapters at the hexagon port" caption="Multiple adapters at the hexagon port" %}

The level of control you have defining the contract of each adapter will vary, and sooner or later there are discussions like "I prefer to use `bar` instead of `foo` for this or that attribute", or one integration requires more attributes than others. Why fighting when you can offer an easy exit for everyone? A better contract for the client using the integration point, and a clean domain model inside the hexagon.

## Preventing information leakage 

There is a more important reason to do an explicit mapping, and it is the leakage of information. It is something that happens rarely but when it happens is very bad at a company level.

Disclaimer: this is just an example to illustrate the situation, I am pretty sure you are able to think about other cases, even much better ones.

To prevent having duplicities and different people doing the same things, the hexagons are reused and that could lead to problems. Lets imaging a different case than the recipes, and think about user profiles. At the beginning a user profile definition could be something like the record below.

```java
public record UserProfile(String id, String name, String surname, ...) {
}
```

Because shit happens, at some point the system evolved, the teams grew up and suddenly because it was necessary for a new internal feature the `internalNotes` attibute added to the model.

```java
public record UserProfile(String id, String name, String surname, String internalNotes, ...) {
}
```

And suddenly we are exposing an internal data to the users. How bad it could be will depend on your business. But mapping to a `UserProfileResponse` that has no `internalNotes` won't expose anything private.

It could be solved using different hexagons for the public use and internal use, but let's be real, some teams are not big enough and using the same hexagon is something that is not that strange (also teams using DDD could be using the same model definition), so at least protect yourself from future scenarios.

## It is just 1 minute

And finally there is the complaint about all the time lost writing the mappers. Well, it is not that much, probably you lost more time reading the last [MonkeyUser strip](https://www.monkeyuser.com/). 

Specially with the modern IDEs and even the use of AI, the mappers are written pretty fast.

## Other cases: Typescript

In the case of Java, the language is very picky about types, but there are other languages that treat classes and interfaces differently, e.g. Typescript or Go.

Take the following code in TypeScript.

```typescript
export class ProfileController {
    public async getProfile(id: number): Promise<ProfileResponse> {
        return profileService.getProfile(id);
    }
}

export class ProfileService {
    public async getProfile(id: number): Promise<Profile> {
        // ... something that returns the requested profile by Id
    }
}

export class ProfileResponse {
    public id!: string;
    public name!: string;
    public surnames!: string;
}

export class Profile {
    public id!: string;
    public name!: string;
    public surnames!: string;
    public internalNotes!: string;
}
```

Because as long as the `Profile` has at least all the attributes from `ProfileResponse` the compiler and IDE won't complaint, and some people uses it as an "advantage" to avoid writing the mapper. Fair enough, **but depending on the framework you are using that doesn't mean that `internalNotes` is not exposed**, because in a lot of cases it is.

What I did at other teams to prevent leaking information, but avoid writing the mappers, is to create a set of integrations tests checking against the actual REST endpoints. But it is tricky because depending on the model definitions and the data you preload for the test there could be cases you won't detect. So my first option is always to create explicit mappers.

## Extra ball

If the boilerplate really gets you mad, but you want to have the explicit mapping, you have options like [MapStruct](https://mapstruct.org/) in Java. Other languages have similar solutions.

## Misc and references

* Photo from <a href="https://unsplash.com/es/@kellysikkema?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Kelly Sikkema</a> in <a href="https://unsplash.com/es/fotos/letras-de-personas-en-papel-de-calco-con-lapiz-mecanico-o2TRWThve_I?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>

## Changelog

* 2024-10-08: Added the extra ball section
