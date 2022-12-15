# TcList
A workaround to have .NET List methods and use them instead of working with raw arrays in TwinCAT

# Structure

Due to the way that TwinCAT treats References of Objects and Interface, in general there are two types of Lists in this project, one for **Objects** (instances of FBs) and another for **Interfaces**.


- ## List of Objects:  

Assume that you have a FB called "X", to have a list of type X that I am going to name it like **List_X_** (C# eq: List< X >) in the documents there are four prerequisites.  

1. A FB called Object who Implements I_Equatable and every FB should be inherited from Object.
2. Three Cast methods in CastHelper FB:
    1. I_EquatableToX  
    2. ListToList_X  
    3. ObjectToX
3. A FB who Implements I_Predicate  
4. A FB who Implements I_Action  

For simplicity I have created a FB called Person and implemented all of those prerequisites. You can make a copy of each one and rename "Person" to your FB (here we call it "X").  
Then you can create a FB (List_X_) who extends List and implement any Protected method of the List FB that you wish to use. This implementation just will include casting businesses, because TwinCAT doesn't support Generic user types.  
Again for simplicity I have created a List_Person_ with full implementation, so you can just make a copy of it and rename "Person" to your FB and use newly created prerequisites of yours.  
Now you can make an instance of your list and enjoy!  


- ## List of Interfaces:  

These are very straight forward compared to List of Objects.  
Assume that you have an Interface called "I_X", Just make a copy of my interfaces list called "List_I_Observer" and rename "I_Observer" to your FB (here we call it "I_X").  
The only prerequisite is a **FB who Implements I_Action**.  
Now you can make an instance of your list (List_I_X_) and enjoy! 
