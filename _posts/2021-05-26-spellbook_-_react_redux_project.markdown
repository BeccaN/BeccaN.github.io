---
layout: post
title:      "Spellbook - React/Redux Project"
date:       2021-05-26 14:06:02 +0000
permalink:  spellbook_-_react_redux_project
---


For my React/Redux project I built a D&D 5th ed. spell managing app that allows user to signup, create spellbooks and then add spells to their spellbook. This allows user to more efficiently see all important information on their characters spells at once in a more visually accesible way. 

There were several technical challenges that I faced during this endeavour, including; building a responsive `react-table` and proper redirection. 

### `react-table` 

If your app requires you to build a responsive table that utilizes grouping, filtering and ordering, I strongly recommend you follow along with [this video guide series.](https://www.youtube.com/watch?v=YwP4NAZGskg&list=PLC3y8-rFHvwgWTSrDiwmUsl4ZvipOw9Cz) Codevolution does a great job of guiding you through building a react table and focuses on various features you can include with your table. `react-table` is a widely used table library for React, it offers a way for developers to create lightweight simple tables. The library utilizes a collection of React hooks and plugins that together build the features and table grid and are returned by the `useTable` hook. 

```
const tableInstance = useTable({ columns, data })
 
 const {
   getTableProps,
   getTableBodyProps,
   headerGroups,
   rows,
   prepareRow,
 } = tableInstance
 
 return (
   // apply the table props
   <table {...getTableProps()}>
     <thead>
       {// Loop over the header rows
       headerGroups.map(headerGroup => (
         // Apply the header row props
         <tr {...headerGroup.getHeaderGroupProps()}>
           {// Loop over the headers in each row
           headerGroup.headers.map(column => (
             // Apply the header cell props
             <th {...column.getHeaderProps()}>
               {// Render the header
               column.render('Header')}
             </th>
           ))}
         </tr>
       ))}
     </thead>
     {/* Apply the table body props */}
     <tbody {...getTableBodyProps()}>
       {// Loop over the table rows
       rows.map(row => {
         // Prepare the row for display
         prepareRow(row)
         return (
           // Apply the row props
           <tr {...row.getRowProps()}>
             {// Loop over the rows cells
             row.cells.map(cell => {
               // Apply the cell props
               return (
                 <td {...cell.getCellProps()}>
                   {// Render the cell contents
                   cell.render('Cell')}
                 </td>
               )
             })}
           </tr>
         )
       })}
     </tbody>
   </table>
 )
```

Above is directly from the React Table docs quickstart guide. This guide does a good job of breaking down the pattern of implementing a basic table. `columns` and `data` are passed into `useTable` hook so that the data accessible and then using built in methods we rendering the data properly.

### Redirection

I used Redirect from `react-router-dom` to handle redirection. The [React Router docs](https://reactrouter.com/web/api/Redirect) explain very well how to use a `<Redirect />`, but I specifically struggled with how my redirects were being hit during the rendering phases. 

At first I was rendering a component based on whether a `props.user` had been passed down to it, but this was causing an undesirable redirection during the DOM compiling phase when `props.user` was null. 

I instead had to utilize JWT `localStorage.getItem("token")` to check if a token existed (a user was logged in) first. 

```
   const spell_books = (props.user) ? props.spell_books.filter(book => book.user_id === props.user.id) : null

  const tokenUserCheck = () => {
    if (localStorage.getItem("token") !== null) { //Check that a token exists
      if (props.user) { //Check that user props exists, required for spell_books 
        return (
          <div className="m-3 my-4 spell-books">
            {spell_books.map(book =>
            <div key={book.id} className="spell-book m-3">
              <Link to={`/spellbooks/${book.id}`} className=""><h2><span>{book.title}</span></h2></Link>
            </div>
            )}
          </div>
        )
      } else {
      return (
        <h3> Loading... </h3> // If token exists but no user props, render this.
      )}
    } else {
      return (<Redirect to="/" />) // If no token exists - no one is logged in, redirect
    }
  }
```

Above is how I handled token checking and user props checking. I couldn't just check for token because the user props data was important for rendering the spel_books that belonged to the logged in user, and just checking for user props was creating a redirect to happen when I didn't want it to. It was important that this redirect be implemented to avoid users from being able to access `url.com/spellbooks` when they weren't logged in. 

### Final Thoughts
These are just two technical "humps" I had to get over during the building of RPG Spellbook. There is still more work to be done, but I am very happy with the outcome of this project so far. To also go back to my first Flatiron CLI project and see how far I have come as a developer is truly remarkable. In previous project builds I felt overwhelmed with technical challenges, but I now feel quite confident in my ability to somehow find a solution that a problem. 
