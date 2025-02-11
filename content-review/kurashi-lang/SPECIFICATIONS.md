# Kurashi Language Specification

Kurashi is a declarative language designed to express goals, weights, achievements, priorities, activities and artifacts. It extends Markdown to include these elements.

Kurashi can be used to create goal documents that can be read as-is in plaintext or viewed as rich text through a Markdown viewer.

Kurashi is also useful when used with tools such as markmap to produce a mindmap to visualize how to achieve the goals. 

> Mindmap visualization placeholder

It can also be used in conjunction with GitHub Copilot and a timeline visualizer such as markwhen. For example, the following prompt can be used to obtain all of the time elements from the goal declaration:

* _Extract all markwhen time elements in this document_

The output can then be rendered by markwhen:

> Markwhen visualization placeholder

GitHub Copilot can also be used to turn the goal declaration document into a "living document" with prompts such as:

* _For each subgoals in root goal, sum the percentages achieved and use the result to replace the percentage achieved for the root goal._
* _Standardize all goal attributes to short form notation_

These prompts can be ran manually by a human or automatically as part of a PR, etc.

Kurashi is a new kind of collaborative protocol and mechanism that does not require any specific application to use, a headless document in the cloud that works usefully because users adheres to the language protocol defined in this document.

## Syntax Overview

### Goals

Goals are specified as Markdown headings or subheadings.

Goals can have subgoals.

The subgoal of a goal (expressed as a Markdown heading) is the subheading of the goal.

Headings (goals) and subheadings (subgoals) are expressed with with #. The level of a goal is determined by the number of #s.

For example:

```
# This is a goal

## This is a subgoal

```
Kurashi follows Markdown's limit of up to 6 level depth in terms of subgoals.

Goals can have attributes specified within round brackets that are appended as postfix, i.e.

```
# This is a goal (Weight: 60%, Achieved: 90%, Priority: 75%)

## This is a subgoal (W: 60%, Achieved:90%)
```
Goal attributes can be specified fully (i.e. Achieved) or with short form notation (i.e. A).

The following shows possible goal attributes and their corresponding short form.

* Weight (W)
* Achieved (A)
* Priority (P)

Goal attributes are optional. A goal can have either one, more than one, or all of the attributes. 

For Weight, Achieved & Priority it is OK for subgoals to have no Weights, Achived or Priority while it's parent have Weight, Achieved & Priority.

Kurashi does not mandate any mathematical correlation between the weight of a goal and its subgoals. The interpretation of the attribute values are left entirely to the users/readers/editors of the Kurashi document. This is to allow flexibility to allow goal definitions like this one:

```
# Travel 100 miles (W: 60%, A: 90%, P: 75%)

## Get a car (A: 100%)

## Fill tank (A: 30%)

```

In the example above, a 100% achievement of the subgoal of getting a car does not equate to a 50% achievement of travelling 100 miles. Therefore, the interpretation of the % achievement (completion) of each goals and subgoals is left completely to the users/readers/editors. 

This also makes it easier for users to commit WIP (Work In Progress) Kurashi compatible documents.

### Activities

Activities are specified simply within goals with markwhen notations.

For example:

```
# This is a goal (Weight: 60%, Achieved: 90%, Priority: 75%)

## This is a subgoal (W: 25%, Achieved:150%)

2025-01-18: Activity that contributes to subgoal #tag

```

Please refer to [Markwhen documentation] for what you can specify as things that happen over time.

### Artifacts

Artifacts are specified simply as Markdown bullet points:

For example:

```
# This is a goal (Weight: 60%, Achieved: 90%, Priority: 75%)

## This is a subgoal (W: 25%, Achieved:150%)

2025-01-18: Activity that contributes to subgoal #tag

* Artifact 1
* [Artifact 2](https://link_to_artifact)
* Artifact 3

```

