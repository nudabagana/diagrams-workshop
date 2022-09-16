# Code your diagrams (productivity)

## 0. Intro
- This will be a short workshop about the usage of diagrams in daily work routine.
-  All information, examples and resources can be found at: https://github.com/nudabagana/diagrams-workshop

## 1. Diagrams
![[UML-Diagram-types-1-1024x658.png]]
- There are 14 most used UML diagrams. 
- Structural can be left for later when there will be a need to document our system (or when planing new architecture). They will **not** be covered in this workshop.
- **Sequence** and **flow** diagrams can be used when creating tasks, especially the ones that require communication between multiple services or just user and any system. 
- Since **easily understandable tasks** save programmers  time and increase their efficiency, this workshop we will be focusing on exactly that. Using sequence and flow diagrams to make tasks easier to understand.
- Sequence diagrams show interaction and its order between processes (in our case, microservices).
- Flow (Activity) diagrams are used to illustrate bussiness or system workflows. It focuses more on the flow of the (business) logic and less on the processes that are doing the logic.
- So Sequence = WHO is interacting with WHO. Flow = WHAT actions have to be done.

## 2. Tooling

- Since everything will be done using regular markdown files (.md) a markdown editor of your choice can be used.
- Some suggestions: 
	- [Obsidian](https://obsidian.md/) - free, multi platform linux/win/mac/android, powerful note keeping tool.
	- [VSCode](https://code.visualstudio.com/) - free, multi platform, kown for most programmers code editing tool. ([with memaid plugin](https://open-vsx.org/extension/bierner/markdown-mermaid))
- For generating diagrams from code, [Mermaid](https://mermaid-js.github.io/mermaid/#/) will be used. Depending on editor selection, it might be already integradet or might need some additional setup. Mermaid also has live editor [here](https://mermaid.live/).
- Mermaid can be used to generate multiple types of diagrams (not only UML). Presentation of different diagrams can be found [here]( https://www.youtube.com/watch?v=rXhUeV5Ko7g).
- If you want to save Mermaid diagram as pdf so anyone could see it, you can either use Obsidian, your own tool or Mermaid live [editor](https://mermaid.live/).
- Bonus: if you want to keep all of your diagrams and notes synced between devices, you can use [Syncthing](https://syncthing.net/). Its Open source, free, multi platform tool for syncing files between devices. Sadly it's out of scope for this workshop.

## 3. Setup your editor
- If you are going to use Obsidian
	- go to https://obsidian.md/, download, install and start your editor.
	- create or open a vault and create new file called "test diagram"
- If you are using any other editor, setup it accordingly and make sure it's working.
- To test: paste this code inside 
\`\`\`mermaid
	flowchart TD  
	Start --> Stop
\`\`\`
- it should show
	```mermaid  
	flowchart TD  
	Start --> Stop
	```

## 4. Sequence diagram

### Information:
1. Shows interaction between objects in time.
2. There are Internal objects and external objects (actors).
3. Line below objects show their lifetime.
4. Activation boxes show their active time (Actors don't have activation boxes).
5. Regular arrow shows call from one object to another.
6. Dashed line shows response.
7. There should be interaction name above every arrow.
8. Interaction lines always go down, which shows their order in time. (up first, down last)
9. If there are multiple responses, then "Alternative box" can be added. It shows different responses based on some param.
10. There should be condition inside "Alternative box"

### Example

![[ATM visit]]

Description:
User goes to an ATM, inserts card. ATM verifies with server if card is valid. Then either asks for PIN or ejects the card.
Also, every 5 mins, ATM asks if user is still there.

### Other examples:
![[Parallel box, nesting boxes]]

![[Critical actions]]

![[Break box]]

![[Colors]]

## 5. Flow diagram

### Information
1. Representation of a process.
2. It has a start and 0-n ends. (round rectangle)
3. It has actions. (rectangle)
4. It can have Inputs/Outputs. (parallelogram)
5. It can have decisions. (diamond/rhombus)
6. Arrows show the direction of the flow.

### Example
![[Count 1 to 9]]

Description: Count from 1 to 9 by odd numbers.

### Other examples

![[Different length links]]

![[Subgraphs]]

## 6. Css styling/ Obsidian fixes
- All mermaid diagrams can be styled using css. More info can be found in their [doccumentation](https://mermaid-js.github.io/mermaid/#/theming).
- If you are using Obsidian with dark theme and encouter style bugs, I suggest using styles below to fix at least some of them.
	- go to settings -> appearance -> CSS Snippets -> Open folder;
	- Create new file "mermaid_fix.css";
	- add code shown below.

```css
.mermaid > svg {
	width: 100%;
}

.mermaid .noteText > tspan {
	fill: black !important;
} 

.mermaid .activation0 {
	fill: black !important;
}

.mermaid .loopLine {
	stroke: #a5a2a2 !important;
}

.mermaid .sequenceNumber {
	fill: black !important;
}
```


## 7. Our workflow

- When designing task which requires communication between different services or BE/FE, **sequence diagram** can be made, exported to pdf or kept as .MD file and added to task. Developer could then see, what endpoints he needs to use/create and what is their input and output.
- When desiging a new feature, **flow diagram** can be used to illustrate what steps need to happen, what input/output can be expected.
- Diagrams should **not** be used for every task. If the task is trivial, requires 0 or only a few endpoints and the flow is clear, diagrams are not needed not to waste time. However if the task complexity is high, diagrams can make it a lot easier to understand.
- Who should make the diagrams? A person who is designing the feature/system implementation. That way we will make sure that task is not even started before having a proper design.
- Some diagrams can even be done by business people (without the inner system knowledge), just to make it easier to understand, what interaction should happen between system and a user.

## 8. Resources

- [Presentation](https://github.com/nudabagana/diagrams-workshop)
- [Markdown syntax](https://www.markdownguide.org/basic-syntax/)
- [Obsidian documentation](https://help.obsidian.md/Getting+started/Create+a+vault)
- [Mermaid documentation](https://mermaid-js.github.io/mermaid/#/README?id=installation)
- [Mermaid live editor](https://mermaid.live/)
- [VSCode](https://code.visualstudio.com/)
- [VSCode Mermaid extension](https://open-vsx.org/extension/bierner/markdown-mermaid)
- [Syncthing](https://syncthing.net/)