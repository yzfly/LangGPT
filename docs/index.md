## Quick Start

You can begin utilizing LangGPT for crafting potent prompts by simply copying and pasting the following file content into GPT-4.
* [LangGPT Helper](https://raw.githubusercontent.com/yzfly/LangGPT/main/LangGPTHelper.md)


## Getting Started

Here, we provide a small `FitnessGPT` example to help you quickly get started with LangGPT. LangGPT offers prompt-writing templates, which you can use to rapidly create high-quality prompts.

```
# Role: FitnessGPT

## Profile

- Author: YZFly
- Version: 0.1
- Language: English
- Description: You are a highly renowned health and nutrition expert FitnessGPT. Take the following information about me and create a custom diet and exercise plan. 

### Create custom diet and exercise plan
1. Take the following information about me
2. I am #Age years old, #Gender, #Height. 
3. My current weight is #Currentweight. 
4. My current medical conditions are #MedicalConditions. 
5. I have food allergies to #FoodAllergies. 
6. My primary fitness and health goals are #PrimaryFitnessHealthGoals. 
7. I can commit to working out #HowManyDaysCanYouWorkoutEachWeek days per week. 
8. I prefer and enjoy his type of workout #ExercisePreference. 
9. I have a diet preference #DietPreference. 
10. I want to have #HowManyMealsPerDay Meals and #HowManySnacksPerDay Snacks. 
11. I dislike eating and cannot eat #ListFoodsYouDislike. 

## Rules
1. Don't break character under any circumstance. 
2. Avoid any superfluous pre and post descriptive text.

## Workflow
1. You will analysis the given the personal information.
2. Create a summary of my diet and exercise plan. 
3. Create a detailed workout program for my exercise plan. 
4. Create a detailed Meal Plan for my diet. 
5. Create a detailed Grocery List for my diet that includes quantity of each item.
6. Include a list of 30 motivational quotes that will keep me inspired towards my goals.

## Initialization
As a/an <Role>, you must follow the <Rules>, you must talk to user in default <Language>，you must greet the user. Then introduce yourself and introduce the <Workflow>.
```
With the help of prompt above, you will create a Role named FitnessGPT, he/her will help you design wonderful personal diet and exercise plan.

### More Examples
Here are more [LangGPT prompts](LangGPT-Prompts.md). The `examples` folder contains LangGPT prompt examples, including prompts and complete conversations with ChatGPT, to help you create wonderful prompt.

* [Code Master CAN](examples/code_anything_now/ChatGPT-Code_Anything_Now_en.md)
* [Xiaohongshu Hit Generator](examples/chinese_xiaohongshu_writer/ChatGPT-Xiaohongshu_Hit_Generator_Conversation.md)
* [Chinese Poet](examples/chinese_poet/ChatGPT-chinese_poet.md)

## Role 

ChatGPT excels at role-playing. By providing role descriptions, role behaviors, and skills, it can produce actions that align well with the role.

Therefore, LangGPT designed the Role template to help ChatGPT better understand user intentions. The Role template is the core of LangGPT.

### Role Template

Here is the markdown Role template:
```
# Role: Your_Role_Name

## Profile

- Author: YZFly
- Version: 0.1
- Language: English or 中文 or Other language
- Description: Describe your role. Give an overview of the role's characteristics and skills

### Skill-1
1.skill description 1
2.skill description 2

### Skill-2
1.skill description 1
2.skill description 2

## Rules
1. Don't break character under any circumstance.

## Workflow
1. First, xxx
2. Then, xxx
3. Finally, xxx

## Initialization
As a/an <Role>, you must follow the <Rules>, you must talk to user in default <Language>，you must greet the user. Then introduce yourself and introduce the <Workflow>.
```

The `Role template` primarily consists of four sections:

* `Profile`: The role's resume, including role description, characteristics, skills, and any other desired traits.
* `Rules`: Rules the role must follow, usually involving actions they must take or avoid, such as "Never break role" and so on.
* `Workflow`: The role's workflow, detailing the type of input users should provide and how the role should respond.
* `Initialization`: Initializing the role according to the Role template's configuration, with most cases requiring only the default content.

A role can be defined and configured using the four sections defined above.

Additionally, if you need to create complex prompts with commands, reminder, and other features, simply add the corresponding sections, as demonstrated in the advanced usage section.

### Steps to Use the Role Template

1. Set the role name: Replace `Your_Role_Name` in `Role: Your_Role_Name` with your desired role name.
2. Write the role's resume in the `# Profile` section:
   * Set the language by specifying `Language` as `中文`, `English`, or any other language, using the target language for expression.
   * Briefly describe the role after `Description`.
   * Add role skills under the `### Skill` section. You can set multiple skills with bulleted descriptions for each skill.
3. Establish rules under `## Rules`: Add rules that the role must follow, typically covering required or prohibited actions, such as "Don't break role under any circumstance," etc.
4. Define the workflow under `## Workflow`: Explain how the role should interact with users, the input users should provide, and how the role should respond.
5. Initialize the role under `## Initialization`: The Role template sets up the role based on the template content, typically without modifications needed.
6. Copy the completed Role template content into the ChatGPT conversation box (or API) and enjoy!

## Advanced Usage

As people continue to explore the capabilities of large models, LangGPT is still under development and refinement. Everyone is welcome to contribute to the LangGPT project, making it easier to use large models.

### Variables

**Variables offer significant versatility in prompt writing, simplifying the process of referencing role content, setting, and modifying role attributes.**

This is an aspect that traditional prompt methods often find challenging to execute.

The `Initialization` part of the Role template makes extensive use of variables:

    As a/an <Role>, you must follow the <Rules>, you must talk to the user in the default <Language>, you must greet the user. Then introduce yourself and introduce the <Workflow>.

In LangGPT, variables are denoted by "<>". The variables here are:
* `<Role>` variable, representing the content of the entire Role.
* `<Rules>` variable, representing the rules in the `## Rules` section.
* `<Language>` variable, representing the value of the `Language` field.

Markdown's hierarchical structure allows ChatGPT to easily identify the content represented by variables:
* Role is the article title, with a scope covering the entire text.
* Rule is a paragraph title, with a scope limited to the paragraph.
* Language is a field with a scope limited to the text specified after the colon.

### Commands

`Commands` make it easy to set some default actions, such as `"/help" to provide help documentation, "/continue" to continue writing text` etc. which are all very useful commands.

* Use '/' as the convention to indicate commands.
* Add the following content to the Role template:
```
## Commands
- Prefix: "/"
- Commands:
    - help: This means that user do not know the commands usage. Please introduce yourself and the commands usage.
    - continue: This means that your output was cut. Please continue where you left off.
```

### Reminder

Using a `Reminder` can help alleviate ChatGPT's forgetting issue.

Add a `Reminder` to the Role template:

```
## Reminder

1. 'Description: You will always remind yourself role settings and you output Reminder contents before responding to the user.'
2. 'Reminder: The user language is language (<language>), rules (<rules>).'
3. "<output>"
```

### Conditional Statements

Use conditional statements just like in programming, with a template like:

If [situation1 happen], you will take [action1], else, you will take [action2]

### Json or Yaml for Convenient Program Development

**Although LangGPT currently employs markdown language, any markup method capable of expressing hierarchical relationships, such as JSON or YAML, can also be utilized.**

Maybe ChatGPT could assist in creating a conversion script?

### Others (TBD)