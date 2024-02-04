![Hamburger View](https://github.com/Mateus-A-Carvalho/responsive-hamburger-menu/blob/main/assets/public/giphy.gif)

# Responsive Hamburger Menu
This respository contains the code of a responsive hamburger menu, using only HTML and CSS. 

## 🚀 Starting!

This is a project of a responsive menu that I learned in this [video](https://www.youtube.com/watch?v=dAIVbLrAb_U&t=1082s) of Web Dev Simplified. In this project, we gonna use only CSS. 

## ⚙ How to use:
The first step os create a `label` element with an `input` element as a child:

### Basic structure

```html
  <label class="hamburger-menu">
    <input type="checkbox"/>
  </label>
```

### Setting main variables to use
After that, going to the CSS file, there are some settings and variables to work on. First of all, we need to set some variables in `:root` pseudo-class.

```css
:root {
  --bar-width: 30px;
  --bar-height: 5px;
  --hamburger-gap: 5px;
  --hamburger-margin: 20%;
  --hamburger-height: calc(var(--bar-height) * 3 + var(--hamburger-gap) * 2);
  --foreground: #2b2b2b;
  --background: #fffffa;
  --animation-timing: .2s ease-in-out;
}
```

+ **`--bar-widht`**: This will set the _width_ of the menu bars;
+ **`--bar-height`**: This will set the _height_ of the menu bars;
+ **`--bar-gap`**: This will set the _gap_ between menu bars;
+ **`--hamburger-margin`**: This will set the _top/bottom_ and _left/right_ positon of menu;
+ **`--hamburger-height`**: This will set the _height_ of all menu; This setting use a calc() CSS function to calculate the _bar-height_ and _hamburger-gap_;
 + **`--foreground`**: This will set the _color_ of _bars_;
 + **`--background`**: This will set the _background-color_ if there is a container wrapping _menu_;
 + **`--animation-timing`**: This will set the _transition time_ to every transition in this menu;
  
### Adjusting width to "X"
  
```css
.hamburger-menu {
  --x-width: calc(var(--hamburger-height) * 1.41421356237);
  display: flex;
  flex-flow: column nowrap;
  gap: var(--hamburger-gap);
  width: max-content;
  cursor: pointer;
  position: absolute;
  top: var(--hamburger-margin);
  left: var(--hamburger-margin);
  z-index: 5;
}
```

Styling the `label` we need to set `--x-width` adjusting the width to be symmetrical to the menu, when it translate to "X". Here we use an trigonometry calculation to get the perfect width.

### Styling pseudo-elements and input

Now, we goona work with `pseudo-elements` and `input` to make three bars for our menu:

```css
.hamburger-menu::before,
.hamburger-menu::after,
.hamburger-menu input {
  content: '';
  width: var(--bar-width);
  height: var(--bar-height);
  background-color: var(--foreground);
  border-radius: 9999px;
  transform-origin: left center;
  transition: 
    opacity var(--animation-timing), 
    width var(--animation-timing),
    rotate var(--animation-timing),
    translate var(--animation-timing),
    background-color var(--animation-timing);
}
```

Here we start to use all variables that we have declared in `:root`

### Styling input

```css
.hamburger-menu input {
  appearance: none;
  outline: none;
  pointer-events: none;
}
```

Here we set some properties to `input` so that lost it's appearrence and looks like a bar;


### Styling bar in "X" 

```css
.hamburger-menu:has(input:checked)::before {
  rotate: 45deg;
  width: var(--x-width); 
  translate: 0 calc(var(--bar-height) / -2); /* Here we set the X position to zero and calculate the height bar and divides for minus two so that before pseudoelement up */
}

.hamburger-menu:has(input:checked)::after {
  rotate: -45deg;
  width: var(--x-width); 
  translate: 0 calc(var(--bar-height) / 2); /*Here we set the X position to zero and calculate the height bar and divides for two so that before pseudoelement down */
}
```

Here we set the the width to the `-x-width` variable to the bars looks symmetrical when `input` is _checked_. Also, we style `translate: 0 calc(var(--bar-height) / 2); ` to the bars stay in correct position. To do this, we set _X axis_ do `0` and _Y Axis_ with a `calc()`, dividing the `--bar-height` to two to superior bar and minus two to inferior bar;

### Styling the input:cheked

Finally, we style `input` when it is checked:

```css
.hamburger-menu input:checked {
  opacity: 0;
  width: 0;
}
```

## Conclusion
I made this repository to share a good hamburger menu with others developers, since not all know to read and learn in english. Teach is the best way to learn. Also, I improved markdown skills writting this documentation. Hope you enjoy!!! 🧑‍💻✋⌨