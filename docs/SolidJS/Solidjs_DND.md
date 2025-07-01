TITLE: Basic Drag and Drop Implementation with Solid DnD
DESCRIPTION: This example demonstrates the fundamental setup for drag and drop functionality using Solid DnD. It involves DragDropProvider and DragDropSensors to establish the D&D context, createDraggable and createDroppable to define interactive elements, and onDragEnd to handle drop events. The Sandbox component illustrates how to create draggable and droppable areas and manage the interaction logic.
SOURCE: https://github.com/thisbeyond/solid-dnd/blob/main/README.md#_snippet_1

LANGUAGE: jsx
CODE:

```
import {
  DragDropProvider,
  DragDropSensors,
  useDragDropContext,
  createDraggable,
  createDroppable,
} from "@thisbeyond/solid-dnd";

const Draggable = (props) => {
  const draggable = createDraggable(props.id);
  return <div use:draggable>draggable</div>;
};

const Droppable = (props) => {
  const droppable = createDroppable(props.id);
  return <div use:droppable>droppable</div>;
};

const Sandbox = () => {
  const [, { onDragEnd }] = useDragDropContext();

  onDragEnd(({draggable, droppable}) => {
    if (droppable) {
      // Handle the drop. Note that solid-dnd doesn't move a draggable into a
      // droppable on drop. It leaves it up to you how you want to handle the
      // drop.
    }
  });

  return (
    <div>
      <Draggable id="draggable-1" />
      <Droppable id="droppable-1" />
    </div>
  );
};

const App = () => {
  return (
    <DragDropProvider>
      <DragDropSensors>
        <Sandbox />
      </DragDropSensors>
    </DragDropProvider>
  );
};

export default App;
```

---

TITLE: Installing Solid DnD Library with npm
DESCRIPTION: This command installs the @thisbeyond/solid-dnd package using npm, making the Solid DnD library available for use in your project. It is the first step to integrate drag and drop functionality into Solid.js applications.
SOURCE: https://github.com/thisbeyond/solid-dnd/blob/main/README.md#_snippet_0

LANGUAGE: bash
CODE:

```
npm install @thisbeyond/solid-dnd
```
