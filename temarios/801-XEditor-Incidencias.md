# 801 XEditor Incidencias

## Id 4754 Invoke the events defined via XSL

### Question

You can tell me how I can relate the events defined in the XSL with the classes that I can define within the project and be able to access them according to the event that it invokes.

I am attaching a file where I describe the problem in detail.

[Questions.pdf](801-XEditor-Incidencias/Questions.pdf)

### Answer

Hi,

when you add elements in the XSL, you have to be very careful. The way you are currently doing this would lead to errors in the Xeditor later on, so I would advise you to do this differently.

For this I have prepared a code snippet for you. In addition, here are always the files and I have explained to you what exactly happens here, so that you can also understand here what happens:

```js
{code:javascript}
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
{code}
```

 Also make sure the `"types_overrides"` will be applied in your `"src/js/index.js" file =>`

Best
Kevin



