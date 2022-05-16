-------only prop drilling using redux in react-app ------
1.at first install redux-toolkit : 6pm I @redux/toolkit, also install react redux binding : npm install react-redux;

2.then create a file in a store>cartSlice.js : here we store data in a small pieces, here
First we initialize a initialState with a empty array, then we have to create a slice for this we have to call createSlice method call also require it like : const{createSlice}=require("@reduxjs/toolkit"); 
Then give a name, give initializeState which we create at first, then create reducers which call the function.
Then create a add and remove function this functions take parameter as a state and action.
Then for add function we push in this empty initialise array : state.push(action.payload);
Then for remove function we remove from the array while checking array element with a id : return state.filter((item) => item.id !== action.payload);
Then export it : export const { add, remove } = cartSlice.actions;
In redux core we create a action, action creator, reducer, store individually but here slice made all of this in a single file,
So also you have to export reducer : export default cartSlice.reducer;
[% action and reducer initialise successfully %]
Now configure store.
                       
3.In store>store.js : at first import : import { configureStore } from '@reduxjs/toolkit';
Then call configureStore method in a store variable and pass slice in reducer object, if you have multiple slice then you can pass here :
const store = configureStore({
    reducer: {
        cart: cartReducer,
        product: productReducer,
    },
});

Then import cartReducer : import cartReducer from './cartSlice';
Then export this store;
[% store initialise successfully %]
Now give access to provider to carry.

4.Then in src>app.js import provider component : import {Provider} from 'react-redux';
Then wrap everything in a provider component and pass a store as a parameter, also import store;
[% provider initialise successfully %]
Now work with consumer or useSelector and useDispatch.

5.In src>components>products.js : in onclick function create a function onClick={() => handleAdd(product)} not like redux core.
In redux core we have a action creator and action so we don't have to create a function just call the function but here we have to create a function and call here.dispatch is action call trigger.
Then create function handleAdd and call dispatch and call action function add add add need payload which is product. For this we need to import add and dispatch and initialise dispatch.
import { useDispatch, useSelector } from 'react-redux';
import { add } from '../store/cartSlice';

 const handleAdd = (product) => {
        dispatch(add(product));
    };
[% dispatch action trigger initialise successfully %]
Now get data.

6.In src/components/navbar.js : for get data we have to import useSelector then take data from this pages states 
  const items = useSelector((state) => state.cart);
And for increment how many products are added then just do {items.length}
7.
8.
9.
10.
11
12.
13.
14.