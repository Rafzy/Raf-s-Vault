#learn 

How does browsers interpret our code to render user interfaces?

Let's say we write this html to be rendered in a browser

```html
<html>
	<body>
		<div>
			<h1>Team</h1>
			<ul>
				<li>A. Loveplace</li>
				<li>G. Hopper</li>
				<li>M. Hamilton</li>
			</ul>
			<button>Like (0)</button>
		</div>
	</body>
</html>
```

The browser then reads the HTML, and constructs the DOM (Document Object Model), that looks like this

![[Pasted image 20250225155227.png]]


**What is the DOM?**

DOM or Document Object Model is a programming interface that represents a web page as a hierarchical structure.

When the browser reads the HTML file it wants to render, it parses the file and creates a tree of nodes (representing the elements, attributes, texts, etc), and each HTML element becomes a node in this tree

The DOM also gives a live representation of the page, it dynamically reflects changes to the page, so if we want to change anything in the page dynamically, we can directly update the DOM via it's API.

**DOM API interaction**

Speaking of DOM's API, the DOM provides methods (`getElementById`, `querySelector`) and properties (`innerHTMl`, `classList`) to manipulate content, structure, and styles.


**HTML vs DOM**

If we look at the DOM inside the browser using the developer tools, it may look different to the original HTML we write, because HTML represents the initial page content, whereas the DOM represents the updated HTML content, which was changed by the javascript we wrote


**What is JSX**

JSX is a syntax extension for javascript that allows us to describe our UI in *html-like* syntax. There are three JSX rules that state how we should structure our syntax in order for it to be acceptable for the transpiler. 
Three JSX Rules:
https://react.dev/learn/writing-markup-with-jsx#the-rules-of-jsx

One of the most popular JSX transpiler is Babel



# React Core Concepts

There are three core concepts of react that is the building blocks of react applications;
- Components
- Props
- State


## Components 

Snippets of code that are self contained, and usually represent building blocks for the full page, kind of like Lego bricks, we can combine these different components together into a larger structure.

This allows us to better maintain our website since we can add more components, update singular components, or delete components without touching the rest of the app.

In react, components are just JavaScript

But there are several rules we have to follow in react components:
- Components should be capitalized in order to disinguish them from plain HTML and javascript
- We also have to use react components like HTML tags, with `<>`

We can also nest components inside each other


## Component Tree

We can keep nesting react components inside of each other, this way we create component trees.

![[Pasted image 20250228130226.png]]

In this component tree, the HomePage is the root (at the top) that nests several components inside it (Header, Article, Footer), and they also nest several components inside, and so on

This modularity allows us to re-use several components inside our application


**Displaying data with propsl**

If we were to re-use our components two times, so far it would display the same thing, but let's say we want to pass in different text, or maybe we don't know the information beforehand, or we want to be able to update that value.

In react, we can use something called `props` and it works similar to HTML's `attributes`, for example the `<img/>` element has `src` attribute which determines the image to be shown.

It works like how a function would work, by creating the component's function that accepts custom arguments that changes the component's behaviors.



**State**

In react, there are a set of functions called **hooks** that allows us to add additional logic to our code, 










