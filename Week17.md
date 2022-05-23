---
title: WEEK 17
subtitle: Design Patterns


caption:
  title: Week 17
  subtitle: Design Patterns
  thumbnail: https://miro.medium.com/max/750/1*94oOQoivKfh4h6sFW7S1iQ.jpeg
---

<div align="left">
Welcome to another Workout-Log blog post! <br>
This week, we are going to have a look on software design patterns and principles. Both are a crucial part of refactoring for an improved software quality maintainability and readability. But of course they are not an ultimate solution  and should be carefully considered before implementing. 

  
  <br><br>
  
  Sidefact: If you want to know why this Blogpost comes so late (Monday 0 o’clock), than you need to read the whole article.
  
    <br><br>
  Here is a great video about design patterns every developer should know: https://www.youtube.com/watch?v=tv-_1er1mWI
  
      <br><br>
For example, here’s a short explanation of the Singleton Pattern: an Singleton is an object that can only be initiated once and this instance is accessed globally. This makes the Singleton pattern perfect for logging activities and is more efficient than always directly using the systems filesystem. Unfortunately, the Singleton pattern does not count for the homework, so we must look at another design pattern.

<br><br>
 So in the following section we’are going to have a look on the prototype pattern: The prototype is a creational Pattern, and its concept is quite similar to the inheritance concept from object oriented programming, but instead of inheriting from an class, a prototype inherits from an object that has already been created. This makes it much easier to share functionality between objects and especially in a dynamic language like JavaScript. Prototypes are also already supported by JavaScript out of the box, so the implementation shouldn’t be a problem for us since our tech stack is using typescript. 
  
  <br><br>
  In our example we have a function for an Array that with activities. This function calculates the sums for each day and puts them in the right position of the array. Instead of calling the function we now want to make a Prototype of the Array Object and add a method for this purpose. Another function for the Array Object that we could consider by implementing as a prototype, would be our custom sorting function, but for the begin we stick with the first one.
  <br><br>
  So next we’ are going to show you why our blog post needed so long. And the reason for this is that we didn’t manage to get the prototype to work in our typescript environment. Below you can see some of our tries to implement the code: 
    <br><br>
  
    Original:
  {% highlight js linenos %}

  calculateDateSums() {
      let days = [];
      let date = new Date(this.Tasks[0].date).toDateString();
      let protein = 0;
      let kcal = 0;
      for (let i = 0; i < this.Tasks.length; i++) {
        let element = this.Tasks[i];
        if (element.type === 'meal') {
          if (new Date(element.date).toDateString() == date) {
            if (!isNaN(Number(element.protein))) {
              protein += Number(element.protein);
            }

            if (!isNaN(Number(element.energy))) {
              kcal += Number(element.energy);
            }
          } else {
            days.push({
              type: 'date',
              index: i + days.length,
              energy: kcal.toString(),
              protein: protein.toString(),
            });
            if (!isNaN(Number(element.protein))) {
              protein = Number(element.protein);
            } else {
              protein = 0;
            }

            if (!isNaN(Number(element.energy))) {
              kcal = Number(element.energy);
            } else {
             kcal = 0;
            }
            date = new Date(element.date).toDateString();
         }
        }
      }
      let index = 0;
      days.forEach((element) => {
        this.Tasks.splice(index, 0, element);
        index = element.index + 1;
      });
    }

{% endhighlight %}  <br><br>

  All the best,<br><br>

  Your workout-log team!<br><br><br><br><br>

</div>

 <script src="https://utteranc.es/client.js"
          repo="DHBW-TrainingApp/Blog"
          issue-term="pathname"
          label="Blog Comment"
          theme="github-light"
          crossorigin="anonymous"
          async>
  </script>
  
  <br>  <br>  <br>  <br>  <br>
  

{:.list-inline}
