# Kurashi Language Specification

Kurashi is a declarative language designed to express goals, weights, achievements, priorities, activities and artifacts. It extends Markdown to include these elements.

Kurashi can be used to create goal documents that can be read as-is in plaintext or viewed as rich text through a Markdown viewer.

Kurashi is also useful when used with tools such as markmap to produce a mindmap to visualize how to achieve the goal. 

> Mindmap visualization placeholder

It can also be used in conjunction with GitHub Copilot and a timeline visualizer such as markwhen. For example, the following prompt can be used to obtain all of the time elements from the goal declaration:

* _Extract all markwhen time elements in this document_

The output can then be rendered by markwhen:

> Markwhen visualization placeholder

GitHub Copilot can also be used to turn the goal declaration document into a "living document" with prompts such as:

* _For each subgoals in root goal, sum the percentages achieved and use the result to replace the percentage achieved for the root goal._

## Syntax Overview

### Goals

Goals are specified as Markdown headings or subheadings.

Goals can have subgoals.

The subgoal of a goal (expressed as a Markdown heading) is the subheading of the goal.

Headings (goals) and subheadings (subgoals) are expressed with with #. The level of a goal is determined by the number of #s.

For example,

```
# This is a goal

## This is a subgoal

```
Kurashi follows Markdown's limit of up to 6 level depth in terms of subgoals.

## Achievements

Achievements are specified as percentages in brackets
