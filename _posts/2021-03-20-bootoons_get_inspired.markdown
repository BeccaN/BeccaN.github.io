---
layout: post
title:      "Bootoons! Get Inspired!"
date:       2021-03-20 13:25:01 -0400
permalink:  bootoons_get_inspired
---


Javascript Project ✔ It is done!

It never ceases to amaze me how much I learn during these project builds. Building apps/side projects is the most important way to practice coding and become a better developer. I can say I definitely learned a TON during this project build, and I'm sure I will learn even more during the next project. Here are some snapshots of what I did learn:

### Create new branches when implementing new components into your app.

Very very important that I'm sure many of us have has to learn the unfortunate tough way... 

Since Oct 1 2020 master branch has changed its name to main. This might bring up some confusion if you are watching any tutorials on this recorded previous to this date. Here is a quick guide on the steps of creating a new branch and then pulling the new branch changes into main. 

1. Create the new branch

`git checkout -b newbranch`
*NOTE: 'checkout' keyword moves you to the new branch, '-b' followed by the branch name is creating the branch.

2. CODE CODE CODE CHANGE CHANGE CHANGE Okay it looks good now!

3. Commit your changes! Push your changes! 
*NOTE: You might have to run this command in order to push changes to github `git push --set-upstream origin styling`

4. I prefer the visual UI of github for this part, so go to your repository on github and click the 'compare & pull request' button ![](https://i.stack.imgur.com/7yscx.pnghttp://)

5. Click on green 'Create pull request' button 

6. Make sure there are no conflicts then click the green 'Merge pull request' button, and then confirm merge.

7. Purple 'merged' status will pop up, then click on 'delete branch' button

8. Back to our code! Switch to the main branch with `git checkout main` and then pull those changes from our new branch that we just merged with `git pull` 

Yay! Now our main branch has all those new changes from the new branch, and while implementing those new changes we never had to worry about breaking our main branch! 

### Use comments to help you navigate your code

This is not only a helpful practice to assist yourselv in navigating your own code, but also for anyone working on your app that is trying to find their way around. Here is an example of how my index.js file is setup:

```
// MANTRA: When some event happens, I want to make what kind of fetch and then manipulate the DOM in what way?
// --global variables-- //
const mainUrl = "http://127.0.0.1:3000/"
const comicCon = document.getElementById("comic-container")
...

// --DOM Loads Event Listener-- //
document.addEventListener('DOMContentLoaded', () => {
   ...
})

// --Add 'category filter' onchange event
function filterHandler() {
   ...
}

// --Fetch for Comics Function-- //
const getComics = function () {
   ...
}

// --Form Handler Function For Post Fetch-- //
const createFormHandler = function (e) {
   ...
}

...```

Also having a pattern/key to your comments for each file could be helpful. For example in my index.js file 
`// --Section Description--//`  vs ` // ***note on something i should change here`. Now I'm communicating a bit more clearly on intent or purpose of the comment. 

### How to implement a category search with OO JS

This is specific to my project, but I feel the way I implemented this feature could potentially be helpful to others. 
 
 I started with creating a select dropdown menu with my categories listed as options. 
```
                <select id="categories">
                    <option value="" disabled selected hidden>categories</option>
                    <option value="humor">humor
                    <option value="scary">scary
                    <option value="romance">romance
                    <option value="slice of life">slice of life
                    <option value="animal">animal
                    <option value="cute">cute
                    <option value="action">action
                    <option value="mystery">mystery
                </select>
```

 I then added an 'onchange' attribute to the select tag
`<select id="categories" onchange="filterHandler()">
...`

The onchange attribute points to a function, filterHandler() which is located in my index.js file
```
function filterHandler() {
    comicCon.innerHTML = ''
    Comic.renderWithCatFilter(catFilter.value).forEach(comic => {
        comicCon.innerHTML += comic.renderComic()
    })
}
```
This functions reads 'empty out the comicCon element (the div where all instances of my main object were being listed), then run the `renderWithCatFilter` static Comic function and pass in the selected value from the dropdown. 
The `renderWithCatFilter()` is located in my comic.js file:
```
  static renderWithCatFilter(category) {
    let filterComics = Comic.all.filter(comic => comic.category == catFilter.value)
    return filterComics
  }
```

In this function I am creating a new array of filtered comics that have the category that was selected from the dropdwn menu. I use the `filter` array function on all instances of Comic object, to build this new `filterComics` array. 
With this array returned the `filterHandler()` function then iterates through each filtered comic and renders each one into the main div where all my comics are being displayed. 

The main takeaway I got from building this category filter functionality, is how to seperate the functions used in their appropriate spaces. The Comic object would only be interested in returning and handling Comic object instances, whereas the index.js file would rather hold the part of the function concerning the returned Comics and then pasting that return onto the DOM. 

### Final Thoughts!
I had a rough start with picking my domain for this project, but now after finishing this project I have so many thoughts and ideas on future projects that I could work on! I look forward to not only the final product of what those ideas can become but also the journey of getting there and what I might learn along the way. 


