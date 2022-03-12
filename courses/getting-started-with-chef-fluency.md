## Understanding Core Chef Principles

## Idempotence

The property of an operation where the same result is achieved when the input parameters are unchanged, regardless of the number of times it is called.

### Idempotence in the world of Chef  
- Resource configuration are defied using discrete actions
- Each action is a declarative statement about a desired result
- Actions are applied against resources
- Result of each action should be consistently predictable

## Convergence

The process of creating a unified state from multiple independent actions

### Convergence in the Context of Chef
- Multiple idempotent actions used to define a desired state
- Desired state applied against resources
- Test-and-repair methodology assesses what actions are needed
- Each resource "converges" on the desired state

## What Is a Chef Recipe?
- Fundamental unit of Chef configuration management
- Authored using Ruby
- Consists of multiple resources, both native and custom
- Can act on external information (e.g. search query)
- Can depend on or be a dependency of other recipes
- Must be stored within a Chef cookbook

 ## The Importance of Ordering
 If you have more than one resource to find, then the order in which you declare these resources matters a great deal.
 - Actions are sequenced in the same order as resources are listed  
 - Resource order creates an implicit success/fail dependency  
 - Resources have an internal order (e.g. multiple actions)

## The Purpose of Default Actions
- Each resource contains at least one actions (e.g. ``` :enable```)
- When calling a resource, you can specify actions (e.g. ``` action :enable```)
- Multiple actions can all be called (e.g. ```action [ :enable, :start ]```)
- If you don't specify an action, the first (i.e. default) action is called

## Understanding Chef Cookbook Structure
- Recipes: Pattern of resources which define end-state
- Attributes: Overwrite existing values on nodes
- Files: distribute files directly to nodes
- Templates: Create node content using dynamic queries
- Metadata: Information about the cookbook (e.g. version)
- Supermarket: Cookbooks from both Chef and the community
