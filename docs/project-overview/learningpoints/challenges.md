# Technical Challenges Overcame
Just like any project, we encountered many technical problems and bugs along the way. This page serves to highlight some of the
more notable ones, and how we overcame them.

<hr/>

### Contenteditable divs and ReactJS
Contenteditable divs are HTML elements whose content is editable after focusing on them. This enables us to build the
seamless-looking UI for the notepage blocks and editable titles, without resorting to HTML form text inputs.

However, these contenteditable HTML elements do not play well with React: whenever React rerenders a component containing a
contenteditable element, the cursor would jump to the end of the line. This is unacceptable for a notetaking app!

Thankfully, after some research, we found a package `react-contenteditable` which handles this cursor jumping issue (to a certain
extent). The tradeoff, as recommended by the library, was that the HTML content was to be stored in a mutable reference (`useRef`)
instead of React state (`useState`) and passed into this component. This is because any rerender triggered higher up the component
tree would still cause the cursor to jump (recall that setting `useState` state triggers a rerender while changing `useRef` state doesn't).
As a result, we needed careful thought and handling of our notepage and database views, and only allow rerenders when it does not
interfere with the cursor positioning.

<hr/>

### Real time 'saving'
In our initial implementation of the real time 'saving' feature, we updated the backend on every keystroke. This was not ideal
as typing a single sentence alone would fire off a dozen or more network requests...

To overcome this, we eventually added a window interval with `window.setInterval()`, and a `hasUnsavedChanges` boolean mutable ref
to check for changes every second or so and update the backend when necessary.

On hindsight, we could have utilized WebSocket, which is a persistent connection between the client and the server where both parties
can start sending data at any time. This would result in lower latency and would fit our notetaking app use-case better.

<hr/>

### 'Laggy' UI while waiting for network requests to resolve
Network requests are slow. This is a problem for our notetaking app, as the user would reasonably expect instantaneous UI updates
for simple CRUD requests like adding a new note, or repositioning a noteblock via dragging. Waiting for the network request to
resolve before we can update the UI with the updated information results in undesirable 'laggy' UI.

Apollo's implementation of GraphQL contains an option for `optimisticResponse`, which follows the *Optimistic UI pattern* (as explained
earlier in the section [here](/noteworthy-documentation/project-overview/learningpoints/skillslearnt/#graphql)). Coupled with the
`update` option, this grants us an easy way of updating our cache, and hence UI, before the network request resolves while handling any
state mismatch thereafter. With this, our UI updates instantaneously as one would expect, while updating the backend too.

<hr/>

### Optimistic UI and 'create' operations
In our initial implementation, we used MongoDB generated IDs in our frontend to identify and fetch notes and databases. This became
a problem when implementing our optimistic UI, as 'temporary IDs' are created while waiting for the network request to resolve with
the actual ID from the backend. Clicking on notes with temporary IDs would result in a note not found error.

To overcome this, we considered a few options, such as using a lower latency WebSocket connection. Ultimately, we decided to simply
add a loading screen if a note with a tempoary ID is clicked, and load the actual page when the optimistic response returns.

<hr/>

### Nestable noteblocks
To allow indentation and nesting in our noteblocks, we had to restructure noteblocks in the backend into a recursively defined document. 
This was a problem when trying to fetch noteblocks as frontend GraphQL query schemas cannot be recursively defined.
To overcome this, the noteblocks tree-like structure had to be flattened and then passed to the frontend as an array. The frontend then
reconverts the array back into a tree.

However another problem arose when passing down props to CRUD handlers due to stale closure of React Hooks. Since we update the 
backend by copying the entire array of noteblocks, CRUD handlers like `addBlockHandler` and `indentBlockHandler` need to be passed props 
containing states of other blocks when updating a single block. These states will get outdated the moment another CRUD handler is triggered. 
To address this problem, we tried using the `onBlur` event handlers to trigger a rerender each time a noteblock loses focus. However, this 
implementation caused visual bugs due to the cursor jumping issue in `react-contenteditable`.

Another problem was that the `react-beautiful-dnd` library used to create draggable blocks no longer works with the new implementation of 
noteblocks as the `Draggable` divs cannot be nested. Due to time constraints, we had to scrap nestable noteblocks for Milestone 3.
