counterflow
===========

I think ReactJS is great but the flux architecture is a bit over-engineered for my taste. I'm using a simpler pattern that seems to work well for my small use cases.

## Conterflow principles: data is global, state is local

 1. There is a global data source (a JSON document) that reflects the state of the document/interface (for example, the minimum set of that for rendering the interface if the user triggers a page reload). This data is stored at a root element. Make a clear distinction between interface state and data: for example, a flag controlling if a modal is open is not data - this kind of state should be stored at some children.
 2. The data source explicitly pass the state to its children using properties - but just the minimum set they must know (this is annoying if you have a deep hierachy of components but a deep hierarchy is probably a code-smell).
 3. The data source will listen for counterflow events, enqueue and handle them. The handlers should strive to be as dumb as possible and just update data; interface logic should reside at components and business logic at the server side.
 4. The only way a component can mutate global data is by emmiting a counterflow event. It is ok for a component to handle his own ephemerous state, including calls to the server API.

 
 

