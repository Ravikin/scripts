---
theme: ravi
---

## You can do pretty code animations
notes:
Hi all, my name is Mateusz. 

As developers, hackers and tinkers we sometimes need to present our code. 
When time comes it is best to make it nice to the eye so our audience won't run away. 

---

How often have you seen this kind of presentations?
![[Pasted image 20231009130947.png]]

---

How often have you seen this kind of presentations?
![[Pasted image 20231009133847.png]]
notes: 
I have to say I did not expect powerpoint to highlight code. It came a long way! Or I just stopped using it after I left school. 

---

What if you need to explain parts of code?<br> For example highlight specific function?
![[Pasted image 20231009133913.png]]
notes:
Are you going to bold it? 

---

What if you need to explain parts of code?<br> For example highlight specific function?
![[Pasted image 20231009133944.png]]
notes:
Wrap it up in rectangle? 

---

What if you need to explain parts of code?<br> For example highlight specific function?
![[Pasted image 20231009134004.png]]
notes:
Change color?

---

### Use Motion Canvas to do it for you!

![[highlights1.mp4]]

notes:
Maybe would you like to simply - highligh - part of code that's responsible for that?

---

## Motion Canvas
Software created by  **@aarthificial**

motioncanvas.io
https://www.youtube.com/@aarthificial

<br />

##### *(all links in the description)*

notes: all of that can be simply created with Motion Canvas type script code

---

#### Motion Canvas can do a lot but I will focus on following
- highlighting
- code additions
- code substractions
- transitions (between scenes)

notes: przeczytaj to

---

## Code Highligh

```ts
  yield * coderef().selection(lines(15, 32),1);
  ^     ^     ^         ^       ^   ^    ^  ^
  |     |     |         |       |   |    |  |
  |     |     |         |       |   |    |  +---- duration 
  |     |     |         |       |   |    +---- end line
  |     |     |         |       |   +----- start line
  |     |     |         |       +----- select lines 
  |     |     |         |     
  |     |     |         +------- highlight
  |     |     |     
  |     |     +--------- reference to code block
  |     |     
  |     +----------- * generator func. frame rendered asap
  |     
  +------------- generate frame
```

notes: 
all commands consist of yield as render either as a generator function or not. 
Generator function with asterisk renders frame instantly while non generator one waits for next render command and is executed simultaneously. 

---

##### Code Block
```ts
<CodeBlock
    ref={coderef}
    fontSize={22}
    fontFamily={'JetBrains Mono'}
    code={() => `That's the code you are looking at right now. 
    that's second line
    third
    and 
    last` }
/>
```
##### How to highlight
```ts
yield * coderef().selection(lines(2, 4),1);
```
##### Highlight will be created for lines 2 to 4 within 1 second. 

notes:
We need to specify code block on which we will be working and then we can use it's reference "coderef" to edit and highlight our code. 

---

### It looks like this

![[highlight2.mp4]]

---

####  Multiple selection

```ts
yield  coderef().selection(lines(2, 4),1);
yield  coderef().selection(lines(15, 32),1);
yield * coderef().selection(lines(24, 29),1);
```

notes:
To select multiple lines you need to buffer selection commands with non generator yield. Then they will be rendered at the same time. 

---

### Everything will happen at once

```ts
yield  coderef().selection(lines(2, 4),1);
yield  coderef().selection(lines(15, 32),1);
yield * coderef().selection(lines(24, 29),1);
```

notes: 
First two lines will take effect in parallel with the third one as `yield *` renders view and `yield` without `*` has to wait for rendering. 
All `yield` statements will be rendered with `yield *`

---

You can also deselect all the lines with following
```ts
yield * coderef().selection([],1);
```
Simple empty selection will highlight nothing.
```ts
yield  coderef().selection(lines(2, 4),1);
yield * coderef().selection(lines(24, 29),1);
```

notes: 
but you can't deselect one of the lines in the same code block. You would need to deselect all and add new selection. 

---

Single words are also doable
```ts
  yield* code().selection(word(20, 40, 2), 0.3);
```

**twenty first** line, starting at the **forty** character, and selecting a total of **two** characters

notes:
This will make a selection on the **twenty first** line, starting at the **forty** character, and selecting a total of **two** characters.

---

which looks like this
<br>
![[higlights3_word.mp4]]

---

## Code addition
Adding, changing and subtracting code in a block of code. 

notes:
We saw all that code being highlighted. 
How to animate changes?

---

### We will use <br>`.edit()`<br/>
Either to **insert** or **remove**
```ts
  yield * coderef2().edit(2)`${insert('cd rtl8812au')}`;
```
```ts
  yield * coderef2().edit(2)`${remove('cd rtl8812au')}`;
```

notes:
Like before we need to grab our code block reference and then we can do whatever we want. Just remember that if you want to preserve already written code you need to include it in the command.

---

```ts
  yield * coderef2().edit(3)`
        <Txt
          ref={label2}
          fontSize={50}
          fontFamily={'JetBrains Mono'}
          fill={'rgba()'}
          text={'Compile${remove(` and install`)}'}
        />
 `;
```

notes: 
just like that. Whole code text needs to be included in the edit statement. Then you can put alterations where you need them. Even multiple.

---

```ts
  yield * coderef2().edit(3)`
        <Txt
          ref={label2}
          fontSize={50}
          fontFamily={'JetBrains Mono'}
          fill={'rgba(${insert(`255, 255, 255, 0.6`)})'}
          text={'Compile${remove(` and install`)}'}
        />
 `;
```

notes: 
insert in the rgba values and removal of text

---

code addition video

notes:


---

## Code removal

code removal clip <br>usuniecie 'and Install'

notes:
this will look something like this example clip


---

 ### You can do it to single words too
 single word video <br>// zmiana 50 na 30

notes:

---

## Scene transitions

---

## Transitions
Occur at the beginning of the scene.

notes: as a bonus I will show you a thing or two about transitions between scenes

---

## Transitions
You can learn more at<br>https://motioncanvas.io/docs/transitions/

notes: the best place to check out is official documentation. There is everything you need to know. 

---

### Transition types
- [`slideTransition`](https://motioncanvas.io/docs/transitions/#slidetransition)
- [`zoomInTransition`](https://motioncanvas.io/docs/transitions/#zoomintransition)
- [`zoomOutTransition`](https://motioncanvas.io/docs/transitions/#zoomouttransition)
- [`fadeTransition`](https://motioncanvas.io/docs/transitions/#fadetransition)

notes:


---

### Custom transitions are also an option!

notes:


---

## Slide Transition


```ts
  import {slideTransition} from '@motion-canvas/core/lib/transitions';
  import {Direction} from '@motion-canvas/core/lib/types';
  
  yield* slideTransition(Direction.Left);
```

notes:


---

### Slides

```ts
  yield* slideTransition(Direction.Bottom, 1);
         + type          + direction       + duration
```

![[transition_examples.mp4]]

notes:


---

### Fade

```ts
  yield* fadeTransition(1);
         + type         + duration
```

![[transition_examples 1.mp4]]

notes:


---

## All of that and more
https://motioncanvas.io<br/>
Go take a look and give author a high five!

notes:


---

He deserves it :) 

notes:


---

Alternative animation software 
- Remotion<br>
	https://www.remotion.dev/
- Animotion<br>
	https://github.com/animotionjs/animotion/
- Manim  3blue1brown icon<br>
	https://www.manim.community

![[Pasted image 20231010203235.png]]

notes:
Manim was created by 3blue1brown to animate his mathematic videos. 

---

![[cropped-cyber_frog_mpiorkowski_icon-1-200x200.png]]
MPIORKOWSKI.COM
# Thank You!

notes:
