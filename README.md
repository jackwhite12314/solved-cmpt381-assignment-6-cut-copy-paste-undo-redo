Download Link: https://assignmentchef.com/product/solved-cmpt381-assignment-6-cut-copy-paste-undo-redo
<br>
In this assignment, you will work with two fundamental types of interaction in visual workspaces – cut/copy/paste, and undo/redo. You will use JavaFX to extend an existing Blob demo and add several interactive capabilities to the system.

<h1>Part 1: Cut/Copy/Paste</h1>

Start with the Blob demo posted to the course Moodle (Examples folder: 381-A6.zip), which implements multiple selection and grouping (note that in this version of the demo, creating new Blobs is done by pressing the ‘a’ key). Add functionality to the application that implements a custom clipboard with three operations: Cut (control-x), Copy (control-c), and Paste (control-v). Your application should meet the following requirements:

Interaction requirements:

<ul>

 <li>When the user presses Control-c, any selected blobs/groups are copied to a custom clipboard (see below for details)</li>

 <li>When the user presses Control-x, the selection is removed from the current model and is placed on the custom clipboard</li>

 <li>When the user presses Control-v, any blobs/groups on the custom clipboard are pasted into the model (and shown in the view)  Pressing Control-v again pastes additional copies of the objects (at the location where they were copied/cut)  When cut/copied and then pasted, any existing group structure in the selection is preserved.</li>

</ul>

Software requirements:

<ul>

 <li>Add code to the controller class to handle the new interaction requirements described above</li>

 <li>Create a new class BlobClipboard to store items that have been cut or copied</li>

 <li>The clipboard object should be created and manipulated in the interaction model</li>

 <li>When copying to the clipboard and when pasting, you will need to make a deep copy of the objects (as described in lectures), because you may be pasting them multiple times, and each paste needs to add different objects to the model  Do not use the Java system Clipboard classes. Implement your own custom class as described above.</li>

</ul>

<table width="703">

 <tbody>

  <tr>

   <td width="234"> After selecting and grouping</td>

   <td width="234"> After cutting with control-x</td>

   <td width="234"> After pasting with control-v</td>

  </tr>

  <tr>

   <td width="234"> After dragging pasted group</td>

   <td width="234"> After pasting again with control-v</td>

   <td width="234"> </td>

  </tr>

 </tbody>

</table>

Resources for part 2:

<ul>

 <li>Details on cut/copy/paste operations: Olsen text, chapter 15</li>

 <li>Tutorial on Java copying: <u>https://dzone.com/articles/java-copy-shallow-vs-deep-in-which-you-will-swim</u></li>

</ul>

<h1>Part 2: Undo/Redo</h1>

In the second part of the assignment, you will extend your system to add the ability to Undo and Redo certain actions in the visual workspace. You will use the Backup Undo approach described in lectures and the text, using the Command pattern.

Additional interface requirements:

<ul>

 <li>Add panels to the left and right of the main workspace</li>

 <li>Each panel contains a Label, a ListView, and a Button</li>

 <li>The left panel shows the current state of the undo stack, and the right panel the state of the redo stack</li>

 <li>Pressing the “Undo!” button executes one undo; pressing the “Redo!” button executes one redo Additional interaction requirements:</li>

 <li>All blob creation, and all blob/group move actions result in the creation of a new BlobCommand object that encapsulates how to undo and redo that action</li>

 <li>Only create and move actions are undoable/redoable. Selection and grouping actions, and cut/copy/paste actions are not undoable/redoable (and it is not required that the selection state match the state of the workspace when a particular action was first carried out).</li>

 <li>Whenever a BlobCommand object is created it is pushed onto the undo stack (and the ListView is updated)</li>

 <li>Whenever the “Undo!” button is pressed, the undo stack is popped and the top BlobCommand’s undo() method is executed. In addition, the BlobCommand is then pushed onto the redo stack.</li>

 <li>When the “Redo!” button is pressed, the redo stack is popped and the top BoxCommand’s doIt() method is executed. In addition, the BoxCommand is then pushed onto the undo stack.</li>

 <li>Note: the markers will only test basic versions of undo and redo, because interleaving creates and moves with grouping actions and cut/copy/paste actions can lead to odd behaviour.</li>

</ul>

Additional software requirements:

<ul>

 <li>Implement the BlobCommand interface (following the example in the text)</li>

 <li>Implement classes MoveCommand and CreateCommand that implement this interface</li>

 <li>Each of these command classes should include a toString() method so that you can put a string representation of the command into the ListView’s list model</li>

 <li>In your InteractionModel, add stack data structures as needed for the undo and redo stacks (you may use the old Java Stack class, or the more modern Deque class)</li>

 <li>You may treat the Application class as the home for the ListViews (you should add methods to the Application class to update the ListViews when the stacks change)</li>

</ul>

This assignment is to be completed individually; each student will hand in an assignment.