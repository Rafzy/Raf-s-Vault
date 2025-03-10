#learn 


> In school, we've learned calculus like it's something to be memorized, now we're going balls deep into the core of calculus, peel off layer by layer the things we've memorized to truly understand the fundamentals of calculus, and how some of the rules of calculus came to be


# Area of a Circle 

Let's start with how the area of a circle was found
we know the formula for the area of a circle as

$$
A = \pi R ^ {2}
$$

But how did this formula came to be?

Let's imagine a circle with a radius of three units
before the knowledge of the formula, how would we think about calculating the area of the circle?
Maybe we can divide the circle into pizza slices, but each pizza slice would be shaped as a triangle and half a circle, still making it hard to estimate

Let's imagine we divide the circle into several inner rings

![[Pasted image 20250223212556.png]]


And let's take a piece of the inner ring, the inner ring would have an inner radius $r$ between 1 and 3.
![[Pasted image 20250223213011.png]]
If we can get the representation for the area of this inner ring, and we can add up all of the inner rings, we may get an idea of what the area of the circle would be

Let's flatten out this inner ring into a long trapezoidal shape 
In reality, the shape of this flattened ring is a trapezoid, but for simplicity sake, let's estimate this area to be a rectangle

![[Pasted image 20250223213146.png]] 

The width of this rectangle is the circumference of the original ring ($2\pi r$), and the thickness depends on how much inner ring we divide the circle into.

For now, let's call the thickness $dr$ for the difference in the radius from one ring to the next
![[Pasted image 20250223213347.png]]

So, approximating the area of this inner ring would be

$$
A \approx 2 \pi r dr
$$

if we can imagine, the smaller the dr, the better the approximation for the area it will be, because the smaller the dr, the more the top and bottom length of this shape will be the same, making it a more rectangular shape than trapezoidal



So, to sum up, we break up the area of the circle into little rings, where the value of r of each ring is between 1 and just before 3 for the biggest ring, each radius of each ring spaced out by the thickness of the rings $dr$. 

if we plot this out with the x axis being $r$, we can see that the spacing for $dr$ corresponds to the thickness of the inner rings

![[Pasted image 20250223214310.png]]

Using this idea, we can fit each of the flattened rings next to each other in the graph, this gives us a better representation of the approximate area for the whole circle

The height of one of the rectangle sitting above some specific value $r$, would be $2 \pi r$
![[Pasted image 20250223214516.png]]


![[Pasted image 20250223214527.png]]


we can draw the graph for the line $2 \pi r$ which is a line with the slope $2 \pi$, and each of the rectangle extends up to the point until it barely touches the graph

![[Pasted image 20250223214724.png]]


remember that the smaller the size of $dr$ is, the better approximation we will get, if we do this for infinitely small $dr$, we see that the total sum of all the rectangles become more like the total area under the graph $2\pi r$

and the area under the graph is just the area of a triangle.

$A = \frac{1}{2}bh$
$A = \frac{1}{2}(3)(2\pi.3)$ 
$A = \pi.3^2$

And so, we get the expression for other radius to be

$$
A = \pi.r^{2}
$$

> But how did that work?

How did we go from approximating the area of sub areas of the circle, into something precise?


There are two important things for $dr$
- 