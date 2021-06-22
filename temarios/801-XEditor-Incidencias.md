# 801 XEditor Incidencias

## ID: 4754 - Invoke the events defined via XSL

### Question

You can tell me how I can relate the events defined in the XSL with the classes that I can define within the project and be able to access them according to the event that it invokes.

I am attaching a file where I describe the problem in detail.

[Questions.pdf](801-XEditor-Incidencias/Questions.pdf)

### Answer

Hi,

when you add elements in the XSL, you have to be very careful. The way you are currently doing this would lead to errors in the Xeditor later on, so I would advise you to do this differently.

For this I have prepared a code snippet for you. In addition, here are always the files and I have explained to you what exactly happens here, so that you can also understand here what happens:

```js
// file: src/js/config/types_overrides.js

// bold = type to override, in your case it would be cita
types.bold.finalizeForFrame = function(editor, element) {
   // check if posibles is set on element
   if (!element.getAttribute('posibles')) {
      return;
   }

   // create a new "frame only" element. This element will only be added to the frame.
   var button = document.createElement("button")
   button.type="input";
   button.innerHTML="Click me";
   button.setAttribute("data-frameOnly", "true");
   button.classList.add('rojo');
   button.addEventListener('click', function() {
      alert("Hello");
      // msg("Hello");
      // editor.configObj.configData.openDialog()
      // here you can execute any logic you want.
   });

   element.getDom().appendChild(button);
}
```

 Also make sure the `"types_overrides"` will be applied in your `"src/js/index.js" file =>`

Best
Kevin

## ID: 4776 - Changes made in the editor over the XML are not reflected

### Question 2

You can tell me how I can update the XML view so that the changes made via code are reflected since they are seen in the Editor but not in the XML.

I am attaching a file where I describe the problem in detail.

[Questions2.pdf](801-XEditor-Incidencias/Questions2.pdf)

### Answer

Hi Adolfo,

here you have to be careful in Xeditor. There are two different types of elements. On the one hand there are elements that only serve for the display, the so-called "Frame Nodes" and on the other hand there are elements that represent the document "Document Nodes". If you want to change the XML or change XML elements in general, you should always do this on the document nodes. An action that is performed on a document node is automatically synchronized to the frame node.

If you want to get to the document node here, it should be enough to add an `element = element.getDocumentNode() || element;` at the beginning of `crearCita`.

Links:
https://api.xeditor.com/v6_8/#!/api/Ext.ux.xeditor.Element-method-getDocumentNode
https://api.xeditor.com/v6_8/#!/api/Ext.ux.xeditor.Element-method-getFrameNode

Best
Kevin

### Question

Effectively placing `element = element.getDocumentNode () || element;` at the beginning of createCitation the XML is updated, the problem I have now is that with `reference.remove();` the node is removed from the XML but not from the Editor, before I deleted it from the editor but not from the XML. You can tell me how to delete it from the Editor.

Also I would like to know if there is more documentation about the product since I only have https://api.xeditor.com/v6_8/ and it lacks examples or a more detailed explanation of how the properties, methods or events should be used, as a reference it is fine when they are already known, but to start working with the product is somewhat complicated.

Best
Adolfo

### Answer


Good morning Adolfo,

it is extremely important that you never work with the DOM element in the Xeditor. You currently do this with `var reference = element.dom`. Just drop the reference and use the element instead of it:

```js
// ....
element.getParent().insertBefore(ancla, element);

// ...
element.removeDeep();
```

if you really want to remove the reference, you should work with `element.removeDeep()`. `element.remove()` does only remove the element itself but keeps its children at the place where the element was. Its more like "unwrapping" the element. You can also use `element.getParent().removeChild(element)` to remove the element and its children.

We additionally have our documentation:
https://documentation.xeditor.com/

And you have the possibility to see the configuration of our demo:

```sh
npm pack @xeditor/xeditor-demo --registry https://npm.xeditor.com
npm pack @xeditor/schema-demo --registry https://npm.xeditor.com
```

In these two folders you will find the configuration in `/src`. In the `index.js` in `@xeditor/xeditor-demo` you can see how the package `@xeditor/schema-demo` is included.

Best
Kevin

## ID: 4780 - Format document (XSL or types_overrides.js)

### Question

I have some problems to get a visual format in the document and doubts when to use XSL or types_overrides.js

I am attaching a file where I describe the problem in detail.

[Questions3.pdf](801-XEditor-Incidencias/Questions3.pdf)

### Answer

Hi Adolfo,

here your answers:

> Should I keep doing the transformations in the XSL files?

My advice is that you only do rudimentary things in XSL. Especially if you have "click" events and the like, then you should always do this in the types_overrides. Also, it is very dangerous to break something in XSL so that the editor throws errors later.

> Or should I just use the types_overrides.js file?

After the initial configuration, we do most of it via the types_overrides. In general, we always recommend using the types_overrides if this is possible and makes sense.

> Or use a combination of both?

The rudimentary configuration always happens via the XSL. Extensions like adding buttons or similar are best done via the types_overrides or in events. Of course, it always depends on what you do.

In general, you should keep the following in mind:

***contenttoeditor.xsl***:

Here, only the XML should be converted to HTML. Try to create only elements with "data-type" and no others. So here really only the XML should become our HTML. No additional HTML elements which are not schema relevant should be inserted.

What is additionally very important to know here is that this logic is executed only once when loading the document. This means that if, for example, a new element is inserted, it would not have the button, because the XSL is not applied here.

***editortocontent.xsl***:

This usually hardly needs to be adjusted. Similar to contenttoeditor.xsl, this one takes care of the transformation from our HTML back to the XML (So just the other direction).

***types_overrides.js***:

With this file you can customize and extend your scheme. Here you can listen for certain events of elements like when they are rendered into the display. If you want to insert buttons that are only meant for opening dialogs or displaying and have no value in the schema, you should *always* do that via types_overrides.js in finalizeForFrame.

The logic in the types_overrides applies to all elements. So for elements which are loaded and for those which are inserted via buttons or other logic in the editor.

For the above reasons I recommend you to have the logic in the types_overrides and not in the XSL

Best
Kevin

## ID: 4785 - refreshing XML

### Question

I'm having some trouble refreshing the XML after retrieving it through a process and refreshing it in the Editor.

I am attaching a file where I describe the problem in detail.

[Questions4.pdf](801-XEditor-Incidencias/Questions4.pdf)

### Answer

Hi Adolfo,

first you can use the following Method to open the *HTML* (XML can not be opened directly):

```js
js
editor.openDocumentByString(editor.documentId, html);
```

to open XML you could use:

```js
editor.getProvider().transformFromXml(editor.documentId, editor.schema, xml, false).then(function(html) {
   editor.openDocumentByString(editor.documentId, html);
});
```

To add a PNG image as icon you have to first create a new CSS Rule in the xeditor.css file:

```css
.icon-neptuno {
   background: url(http://es006-ppdapp001:8080/Helios2/images/neptuno.png);
   background-size: contain;
}
```

Now you can use the 'icon-neptuno' in the `icon` property.

Best
Kevin


## ID: 4796 - Is there any way to search for a node type within the document

### Question

There is some way to search for a type of node within the document no matter what level of the document it is at.

I need to know how many types of nodes there are of type "NOTE" in order to assign an attribute "id" depending on the number of nodes "NOTE" which can be found at any level of the document. For which I need to know if there is any instruction that reports this information to me

### Answer

Hey,

You can use the method `findChildrenByTypes` for this. This will search recursively for elements of the given type. So, if you call this on the root element, you will receive all elements of given type within the document. findChildrenByTypes will return a NodeList, which has a build in getCount method.
So, an example call might look like this:

```js
var root = editor.document.root;
var targetElements = root.findChildrenByTypes(false, ['note']);
var count = targetElements.getCount();
```

I hope this helps.

Best wishes,
Sascha

## ID: 4800 - Move through the document

### Question

I need to move through the document

I am attaching a file where I describe the problem in detail.

[Questions5.pdf](801-XEditor-Incidencias/Questions5.pdf)

**NOTA**

I have found that with the JS statement

```js
Element.scrollIntoView()
```

https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView

I can move to a certain item on the screen.

```js
types.nt.finalizeForFrame = function(editor, element) {

   // change value id for new node NT
   var root = editor.document.root;
   var targetElements = root.findChildrenByTypes(false, ['nt']);
   var id = 0;
   if(targetElements.getCount() > 0){
      var lastNT = targetElements.getLast();
      id = lastNT.getAttribute('id');
      ++id;
   }else{
      id = 1;
   }

   //create button
   var button = document.createElement("button")
   button.type="input";
   button.innerHTML= id;
   button.title = id;
   button.setAttribute("data-frameOnly", "true");
   button.classList.add('verde');
   button.classList.add('botonXopus');
   button.addEventListener('click', function() {
      element.getDom().scrollIntoView(true);
   });
   element.getDom().append(button);
};
```

If I use the above code it works.

But if instead of using element, I first look for another different element and try to move to said element it doesn't work anymore,

```js
types.np.finalizeForFrame = function(editor, element) {

   var root = editor.document.root;

   // Retrieve all NT items to get the max ID
   var ntElements = root.findChildrenByTypes(false, ['nt']);

   var firstNT = root.findFirstChildByTypes(true,['nt']);
   console.log("firstNT " + firstNT.getDom());

   // read value id for put to button
   var id = 0;
   if(ntElements.getCount() > 0){
      var lastNT = ntElements.getLast();
      id = lastNT.getAttribute('id');
   }else{
      id = 1;
   }

   //Crea el botón
   var button = document.createElement("button");
   button.type="input";
   button.innerHTML= id;
   button.title = id;
   button.setAttribute("data-frameOnly", "true");
   button.classList.add('verde');
   button.classList.add('botonXopus');
   button.addEventListener('click', function() {

      //element.getDom().scrollIntoView(true);
      firstNT.getDom().scrollIntoView(true);
   });

   //Obtiene referencia para añadir antes el botón
   var primerHijo = element.findFirstNodeChild();
   element.insertBefore(button, primerHijo);
};
```


It only works well with element that arrives as a parameter because it seems that when I retrieve an element, it does not recover it completely well.

In theory firstNT is the same as "element" in the first case but in the second case it does not move towards it.

Some clue???

### Answer

I wrote a simple sample snippet, which does something similar: It selects the last paragraph in our demo document. The following code does the trick:

```js
// Dummy code to get last paragraph element, which is used in this example as a target
// This has to be adapted to extract the target element you want to select
var paras = editor.document.root.findChildrenByTypes(false, ['p']);
var target = paras.getLast();

// GENERAL LOGIC THAT CAN BE REUSED STARTS HERE

// select element
// second argument indicates whether start or beginning of element should be selected
editor.selectionManager.selectElement(target, true);

// sync selection and update editor state
editor.selectionManager.sync();
editor.updateState();

// if selection is out of viewport, we'll scroll to it and sync selection again
var scrollResult = editor.contentFrame.scrollToSelection('middle', true);
if (scrollResult.selectionCorrected) {
   editor.updateState();
   editor.selectionManager.sync();
}
```

I hope the comments help clarifying how exactly this works and can be adjusted to your needs.

Best wishes,
Sascha

## ID: 4801 - Strange behavior when deleting an Item

### Question

When trying to delete an element, a cycle is carried out where it eliminates all the similar elements that I have in the document, so instead of deleting a single element it deletes all the existing ones.

I have encountered this behavior in XEditor on other occasions and I don't understand why this happens.

In the attached document I show a small example and how it affects the desired behavior, to facilitate the understanding of the problem and can provide me with a possible solution.

[Questions6.pdf](801-XEditor-Incidencias/Questions6.pdf)

### Answer

Hi,

To me it looks like the document is already invalid when opened. The first delete action causes Xeditors build in validation to go through the Element the action was performed in. Xeditor will remove elements that are not valid according to the schema (either in general, or at least at the current position).

A quick test to confirm this would be to call the following code after the document was opened:

```js
editor.document.root.fixState(true);
```

By calling `fixState` on the root element, a complete validation will be performed and all invalid elements would be removed. Can you confirm that by doing this, the elements are removed as well? This would help a lot with further investigation.

Best wishes,
Sascha


## ID: 

### Question

### Answer


## ID: 

### Question

### Answer


## ID: 

### Question

### Answer


## ID: 

### Question

### Answer


## ID: 

### Question

### Answer




