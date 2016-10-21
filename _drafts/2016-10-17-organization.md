---
---
# Organization

So far I have a few raw js objects logged to the console.  I've got some actions being dispatched and can see the redux store after each one to check that the actions are having the expected effect.

But this is all in my `app.js` file.  Unsuitable going forward.

My next task will be to set up some folders so that I can have multiple examples and components within each and `app.js` will be a wee small bootstrap to kick things off.

Oh, and reducer composition looks good to add in at this point as well, before we get much further along.

## What I found

[This](http://redux.js.org/docs/recipes/reducers/BeyondCombineReducers.html#sharing-data-between-slice-reducers) bit of helpfulness in the Redux docs covers exactly what I was looking for (via [this](https://github.com/reactjs/redux/issues/749)).  Specifically, in my tic-tac-toe example I need to know who the current player is in the implementation of the `board` reducer in order to update the indicated cell with the proper value.

So while I'd initially thought to use `combineReducers`, I'll instead write a simple custom root reducer.

## Side note

I found while trying to use `react-router` on an unrelated project that one of the dependencies didn't install.  Thinking of grabbing a fresh copy I deleted the `node-modules` folder and tried `npm install` again.  I overheard someone mention that if you run `npm cache clean` that it will clear the cached version and force npm to go download a fresh copy.  This may help (it did help the other guy) if any of the dependencies had a corrupt file.
