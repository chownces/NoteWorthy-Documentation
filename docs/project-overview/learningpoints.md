# Learning Points
Just like any project, we encountered many technical problems and bugs along the way. This page serves to highlight some of the
more notable ones, and how we overcame them.

#### Categories implementation
When implementing boardview for Noteworthy, categories were added as has-a attribute of the Note document in the backend. However 
this made it difficult to correctly reorder notes within their categories inside boardview. This problem was fixed by creating a 
Category document and making an array of notes a has-a attribute of Category.

#### React DnD bug
We encountered this bug when creating draggable notes within boardview. The draggable components worked only the first time, and the
page had to be refreshed for it to work again. It took us a while to realise that the bug was due to missing unique key property in 
the draggable components.

#### Laggy react DnD.
We opted to use apollo cache as the way to track state in draggable components. This gave rise to lag and the draggables would pop
back and forth between their new and old positions after a drag. This was solved by using apollo's optimistic response during
mutations created by a drag.

#### Laggy deployment (unsolved).
Our vercel deployment was laggy, and any action would take a few seconds to load. We tried to counter this by using apollo's 
optimistic response. However, any action creating a new document in the backend causes issue as a temporary document is created. 
Performing any action on these temporary documents throws an error since these documents actually do not exist in the backend.

#### Cursor management of contenteditable divs in React
When implementing our note blocks, which use contenteditable divs, a React rerender triggered by setState changes interferes with the
positioning of the cursor (jumps to the end of line). To overcome this, we use the package react-contenteditable (which is a wrapper
component for contenteditable HTML), and track our state in React mutable refs instead of React useState. This would prevent rerenders
from being triggered outside react-contenteditable components, and allows react-contenteditable to handle the cursor within the block.
