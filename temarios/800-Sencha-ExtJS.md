![image](https://user-images.githubusercontent.com/23094588/119517890-4c5fbd00-bd78-11eb-92e6-17cfb7c61b69.png)

![image](https://user-images.githubusercontent.com/23094588/119518302-b0828100-bd78-11eb-90ed-9edcc3aef7e6.png)

![image](https://user-images.githubusercontent.com/23094588/119518711-11aa5480-bd79-11eb-9645-a0b5753309ca.png)

![image](https://user-images.githubusercontent.com/23094588/119518941-47e7d400-bd79-11eb-8d86-0b5ae82e8242.png)

![image](https://user-images.githubusercontent.com/23094588/119519121-749beb80-bd79-11eb-92a1-5fc67cb44ff9.png)


```html
<%@ page language="java" pageEncoding="UTF-8"%>
<%@ taglib prefix="s" uri="/struts-tags" %>
<%@ taglib prefix="sj" uri="/struts-jquery-tags"%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
	<head>
		<s:head/>
		<sj:head locale="es" jqueryui="true" jquerytheme="%{getText('tema.jquery')}"/>

		<script type="text/javascript" src="<s:url value="/js/comun.js"/>"></script>

	   	<link href="<s:url value="/css/estilosXopus.css"/>" rel="stylesheet" type="text/css" />
	   	
	   	<script>
		   	window.onload = function() {
		   		
		   		var node = parent.dialogArguments.node;
		   		var urlImagen = parent.dialogArguments.value; 

		   		var imagen = node.selectSingleNode("//imagenes/imagen[@nombre = '"+urlImagen+"']");
		   		
				if (imagen != null) {
					$("#thumbnail").attr("src", "data:image/jpeg;base64,"+imagen.getAttribute("contenido"));
				} else if (urlImagen != "") {
   		            $("#thumbnail").attr("src", replaceHost(urlImagen));
		   		}
		   		
		   		$("#ancho").val(node.getAttribute("width"));
		   		$("#alto").val(node.getAttribute("height"));
		   		$("#titulo").val(node.getAttribute("title"));
		   		$("#textoAlternativo").val(node.getAttribute("alt"));
		   	};
	
	   		function aceptar() {
	   			
	   			if ($("#fichero").val()) {
		   			var nodoEdicion = parent.Editor.getActiveDocument().selectSingleNode("/edicion");
		   			
		   			var formData = new FormData($("#formUpload")[0]);
		   			formData.append("idDocumento", nodoEdicion.getAttribute("idDocumento"));
		
		   		    $.ajax({
		   		        url: "subirImagen",
		   		        type: "post",
		   		        data: formData,
		   		        async: false,
		   		        success: function (data) {
		   		        	
		   		        	if (data.url) {
		   		        		//Se comprueba si la imagen anterior estaba embebida, en cuyo caso se elimina el contenido
   		        				var imagen = nodoEdicion.selectSingleNode("xml-fragment/imagenes/imagen[@nombre = '"+parent.dialogArguments.value+"']");
		   		        		
								if (imagen != null) {
									imagen.getParentNode().removeChild(imagen);
								}

								parent.choose({
							  		src: data.url,
							  		width: $("#ancho").val().trim()?$("#ancho").val().trim():null,
							  		height: $("#alto").val().trim()?$("#alto").val().trim():null,
							  		title: $("#titulo").val().trim()?$("#titulo").val().trim():null,
							  		alt: $("#textoAlternativo").val().trim()?$("#textoAlternativo").val().trim():null
						  		});
		   		        	} else {
		   		        		$("#errorSubida").html(data.error);
		   		        		$("#errorSubida").css("display", "block");
		   		        	}
		   		        },
		   		        cache: false,
		   		        contentType: false,
		   		        processData: false
		   		    });
	   			} else if (parent.dialogArguments.value != ""){
			  		parent.choose({
			  			src: parent.dialogArguments.value,
				  		width: $("#ancho").val().trim()?$("#ancho").val().trim():null,
				  		height: $("#alto").val().trim()?$("#alto").val().trim():null,
				  		title: $("#titulo").val().trim()?$("#titulo").val().trim():null,
				  		alt: $("#textoAlternativo").val().trim()?$("#textoAlternativo").val().trim():null,
			  		});
	   			} else {
	   				parent.dialogArguments.node.getParentNode().removeChild(parent.dialogArguments.node);
	   				parent.Editor.getModalDialog().close();
	   			}

	   		}
	   		
	   		function preview(input) {
	   			
	   			if (input.files && input.files[0]) {
	   		        var reader = new FileReader();

	   		        reader.onload = function (e) {
	   		            $("#thumbnail").attr("src", replaceHost(e.target.result));
	   		        }

	   		        reader.readAsDataURL(input.files[0]);
	        		$("#errorSubida").css("display", "none");
	   		    }
	   		}
	   	</script>
	   	
	</head>

	<body>
		<s:form id="formUpload" name="formUpload" method="POST" enctype="multipart/form-data" theme="simple" action="subirImagen" >
			<table>
			<tr>
				<td>
					<s:label for="titulo" key="titulo"/>
				</td>
				<td>
					<s:textfield name="titulo" id="titulo" size="50"/>
				</td>
			</tr>
			<tr>
				<td>
					<s:label for="textoAlternativo" key="textoAlternativo"/>
				</td>
				<td>
					<s:textfield name="textoAlternativo" id="textoAlternativo" size="50"/>
				</td>
			</tr>
			<tr>
				<td>
					<s:label title="%{getText('ayuda.fichero.img')}" for="fichero" key="fichero"/><s:file id="fichero" name="fichero" accept="image/jpeg,image/gif,image/png" title="%{getText('ayuda.fichero.img')}" size="50" labelposition="top" onchange="preview(this)"/>
					<div id="errorSubida" style="display:none" class="marcoXopus rojo"/>
				</td>
				<td rowspan="2">
					<img id="thumbnail" src="" alt="Vista previa" class="thumbnail" style="min-width: 100px; min-height: 100px;max-width: 200px; max-height: 200px;"/>
				</td>
			</tr>
			<tr>
				<td>
					<s:label for="ancho" key="ancho"/><s:textfield name="ancho" id="ancho" size="4"/>
					<s:label for="alto" key="alto"/><s:textfield name="alto" id="alto" size="4"/>
				</td>
			</tr>
			<tr>
				<td colspan="2">
					<sj:a button="true" onclick="aceptar();" cssClass="botonSmall" cssStyle="margin-top: 20px;float: right;"><s:text name="Aceptar"/></sj:a>
				</td>
			</tr>
			</table>
		</s:form>
	</body>
</html>
```


IMAGE-LOAD-EXAMPLE

```html
<!DOCTYPE html>
<html>
   <head>
    <title>ComboBox - Multiple Selection</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {

            Ext.define('StateModel', {
                  extend: 'Ext.data.Model',
                  fields: ['id', 'abbr', 'state', 'description', 'country']
            });

            var store = Ext.create('Ext.data.Store', {
                  model: 'StateModel',
                  proxy: {
                     type: 'ajax',
                     url: 'states.json',
                     reader: {
                           type: 'array',
                           root: 'data'
                     }
                  }
            });
            store.load();

            // Crear el combo box, attached al data store de los estados
            var cb = new Ext.create('Ext.form.ComboBox', {
                fieldLabel: 'Seleccionar varios estados',
                store: store,
                value: ['AL', 'AK', 'AR'],
                queryMode: 'remote',
                displayField: 'state',
                valueField: 'abbr',
                width: 500,
                labelWidth: 130,
                padding:'5px',
                multiSelect: true,
                forceSelection: true,
                //renderTo: Ext.getBody(),
            });

            Ext.create('Ext.form.Panel', {
               renderTo: document.body,
               title: 'Formulario de Usuario',
               height: 350,
               width: 800,
               bodyPadding: 10,
               defaultType: 'textfield',
               url: 'http://familiadelarosa.com/950-ExtJS-6-2-0/serverside/add_user_02.php',
               items: [
                  {
                        fieldLabel: 'Nombre',
                        name: 'firstName',
                        labelWidth: 130
                  },
                  {
                        fieldLabel: 'Apellido',
                        name: 'lastName',
                        labelWidth: 130
                  },
                  {
                     xtype: 'combobox',
                     fieldLabel: 'Seleccionar varios estados',
                     store: store,
                     value: ['AR'],
                     queryMode: 'remote',
                     displayField: 'state',
                     valueField: 'abbr',
                     width: 500,
                     labelWidth: 130,
                     padding:'5px',
                     forceSelection: true
                  }
               ],
               buttons: [
                  {
                     text: 'Submit',
                     handler: function() {
                        var form = this.up('form'); // obtener el form panel
                        if (form.isValid()) { // asegúrese de que el formulario contenga datos válidos antes de enviar
                           form.submit({
                                 success: function(form, action) {
                                    Ext.Msg.alert('Éxitoso', action.result.msg);
                                 },
                                 failure: function(form, action) {
                                    Ext.Msg.alert('Fallido', action.result.msg);
                                 }
                           });
                        } else { // display error alert if the data is invalid
                           Ext.Msg.alert('Datos no válidos', 'Corrija los errores de formulario')
                        }
                     }
                  }
               ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```


IMAGE-UPLOAD-USING-EXTJS

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- https://fiddle.sencha.com/#view/editor&fiddle/30pp -->
        <title>FORM SUBMIT</title>
        <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
        <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
            rel = "stylesheet" />
        <script type = "text/javascript" 
            src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
        <script type = "text/javascript">
            // Image Upload Example
// In this example we show the Form Panel along with some commonly used
// input fields available from Ext JS.  But, we've also added a little bit
// of additional functionality to show how the Form Panel can be easily
// upload images using Extjs filefield.


Ext.application({
    name: 'Fiddle',

    launch: function() {

        if (!Ext.getStore("imagesUploadStore")) {
            Ext.create('Ext.data.Store', {
                id: 'imagesUploadStore',
                fields: [{
                    name: 'src'
                }, {
                    name: 'imageId'
                }]
            });
        }
        Ext.getStore("imagesUploadStore").removeAll();

        var form = Ext.create({
            xtype: 'form',
            renderTo: Ext.getBody(),
            title: 'Image Upload Form',
            margin: 20,
            bodyPadding: 12,
            width: 500,
            items: [{
                xtype: 'fieldcontainer',
                layout : 'hbox',
                items : [{
                            xtype: 'label',
                             margin : '5 0 0 10',
                            name: 'imagesLabel',
                            text: 'Images'
                        },
                        {
                            xtype: 'label',
                            margin : '5 0 0 15',
                            name: 'imageCount',
                            text: '0 image(s) attached'
                        },{
                            xtype: 'filefield',
                            hidden: true,
                            buttonText: 'AddImage',
                            width: 90,
                            name: 'file',
                            itemId: 'file',
                            buttonOnly: true,
                            listeners: {
                                afterrender: function(filefield) {
                                    filefield.fileInputEl.dom.multiple = true
                                },
                                change: function() {
                                    var files = event.target.files;

                                    for (var i = 0, f; f = files[i]; i++) {

                                        if (!f.type.match('image.*')) {
                                            continue;
                                        }

                                        var reader = new FileReader();

                                        reader.onload = (function(theFile) {
                                            return function(e) {
                                            	var attachimage = false;
                                                var imgStore = Ext.data.StoreManager.lookup('imagesUploadStore')
                                                var imgStoreLength = imgStore.data.items.length;
                                                if (imgStoreLength === 0) {
                                                    imgStore.loadData([{
                                                        'src': e.target.result,
                                                        'imageId': Math.random()
                                                    }], true);
                                                } else {
                                                    for (var idx = 0; idx < imgStoreLength; idx++) {
                                                        if (e.target.result === imgStore.data.items[idx].data.src) {


                                                            return;
                                                        } else {
                                                            attachimage = true;
                                                        }
                                                    }
                                                    if (attachimage === true) {
                                                        imgStore.loadData([{
                                                            'src': e.target.result,
                                                            'imageId': Math.random()
                                                        }], true);
                                                    }

                                                }

                                                var img = Ext.ComponentQuery.query('#imgView')[0];

                                                img.setStore(imgStore);
                                                img.refresh();

                                            };
                                        })(f);

                                        // Read in the image file as a data URL.
                                        reader.readAsDataURL(f);
                                    }
                                }

                            }
                        },{
                            xtype: 'button',
                            margin : '0 0 0 20',
                            text: 'Attach/Remove Images...',
                            listeners: {
                                click: function(){
                                    Ext.create('Ext.window.Window',{
                                  	modal: true,
                        			title: 'Image Upload',
                        			titleAlign: 'center',
                        			constrain: true,
                        			autoDestroy: false,
                        			closeAction: 'hide',			
                        			closable: true,
                        			width: 700,
                        			height: 400,
                        			bbar:[{ xtype: 'button', text: 'Done' ,handler:function(){}}],
                        			tbar: [{xtype: 'button', text: 'Remove',itemId:'removebtnId',disabled:true,listeners : {
                        			
                        			            click : function(){
                                            	    		   var selectedImg= Ext.ComponentQuery.query('[itemId=imgView]')[0].getSelection();
                                            	    		   var imgStore = Ext.getStore('imagesUploadStore');
                                            	    		   imgStore.remove(selectedImg);
                                            	    		   Ext.ComponentQuery.query('[itemId=removebtnId]')[0].disable();
                                            	    		   var img= Ext.ComponentQuery.query('#imgView')[0];
                                            	    		   img.refresh();
                                            	    	   }
                        			       }},
                        	    	       {xtype: 'button', text: 'Browse',cls:'imgBrowseCls',listeners : {
                        	    	           click : function(){
                            	    			   var uploadButton = Ext.ComponentQuery.query('#file')[0];
                            	    			   uploadButton.el.dom.getElementsByTagName('input')[1].click();
	    		   }    	    	       } }
                        	    	   ],
                                    items:[{
                    	    		   xtype : 'dataview',
                    	    		   itemId :'imgView',
                    	    		   scrollable : true,
                    	    		   store: Ext.data.StoreManager.lookup('imagesUploadStore') ,
                    	    		   width : 700,
                    	    		   deferEmptyText: false,
                    	    		   itemSelector: 'div.thumb-wrap',
                    	    		   multiSelect: true,
                    	    		   selectedCls:'imgSelctCls',
                    	    		   tpl: [
                    	    		         '<tpl for=".">',
                    	    		         '<div  class="thumb-wrap">',
                    	    		         '<div style ="float :left;"><img class="imgUploadCls" src="{src}" ></div>',
                    	    		         '</div>',
                    	    		         '</tpl>'
                    	    		         ],
                    	    		         height: 310,
                    	    		         emptyText: '<div style="text-align: center;">No images to display.</div>',
                    	    		         listeners : {
                    	    		        	 select: function(){
                    	    		        	
                    	    		        	      var selectedImg= Ext.ComponentQuery.query('[itemId=imgView]')[0].getSelection();
                    	    		        		 if(selectedImg.length>0 ){
                    	    		        			 Ext.ComponentQuery.query('[itemId=removebtnId]')[0].enable();
                    	    		        		 }
                    	    		        		 else{
                    	    		        			 Ext.ComponentQuery.query('[itemId=removebtnId]')[0].disable();
                    	    		        		 }
                    	    		        	
                    	    		        	 },
                    	    		        	 deselect:function(){
                    	    		        	     Ext.ComponentQuery.query('[itemId=removebtnId]')[0].disable();
                    	    		        	 }
                    	    		        }
                    	    	        }]
                                     }).show();
                                }
                            }
                        }]
            }]
        });


    }
});
        </script>
    </head>   
    <body></body>
</html>
```

IMAGE-WIDTH-HEIGHT

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- https://fiddle.sencha.com/#view/editor&fiddle/30pp -->
        <title>FORM SUBMIT</title>
        <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
        <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
            rel = "stylesheet" />
        <script type = "text/javascript" 
            src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
        <script type = "text/javascript">
            Ext.application({
    name : 'Fiddle',

    launch : function() {
        Ext.create('Ext.Img', {
            src: 'https://www.sencha.com/wp-content/uploads/2019/06/productPage-tab-develop-ExtJS-KitchenSink.png',
            style: {
                maxWidth: "50px",
                maxHeight: "70px",
            },
            listeners: {
                render: function() {
                    this.mon(this.getEl(), 'load', function(e) {
                        var w = this.getWidth();
                        var h = this.getHeight();
                        // Center vertically/horizontally
                        this.setX(Math.round((100 - w) / 2));
                        this.setY(Math.round((100 - h) / 2));
                        
                    });
                }
            },
            renderTo: Ext.getBody()
        });
    }
});
        </script>
    </head>   
    <body></body>
</html>
```

IMAGEUPLOADER

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- https://fiddle.sencha.com/#view/editor&fiddle/30pp -->
        <title>FORM SUBMIT</title>
        <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
        <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
            rel = "stylesheet" />
        <script type = "text/javascript" 
            src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
        <script type = "text/javascript">
            Ext.application({
                name: 'Fiddle',
                launch: function () {
                    new Ext.container.Container({
                        renderTo: Ext.getBody(),
                        width: 400,
                        height: 400,
                        layout: {
                            type: 'vbox',
                            align: 'stretch'
                        },
                        viewModel: {},
                        items: [
                            {
                                xclass: 'Ext.form.field.File',
                                fieldLabel: 'Choose Picture',
                                listeners: {
                                    change (field) {
                                        const dom = Ext.getDom(field.fileInputEl);
                                        const container = field.up('container');
                                        const viewModel = container.getViewModel();
                                        const reader = new FileReader();

                                        reader.onload = e => viewModel.set('imgData', e.target.result);

                                        reader.readAsDataURL(dom.files[ 0 ]);
                                    }
                                }
                            },
                            {
                                xclass: 'Ext.Img',
                                flex: 1,
                                bind: {
                                    src: '{imgData}'
                                }
                            }
                        ]
                        
                    })
                    , Ext.define('com.view.common.ImageViewer', {
                        extend: 'Ext.panel.Panel',    
                        xtype: 'imageviewer',
                        autoScroll : true,
                        layout: 'border', 
                        items:[{
                            xtype: 'displayfield',
                            cellCls: 'fo-table-row-td',
                            fieldStyle: 'text-align:center; font-size:large; font-weight:bold;',
                            value : 'No Image!'
                        }],
                        initComponent: function () {
                            var me = this;
                            if(Ext.isEmpty(me.__PARAMS)){
                                me.callParent(null);
                                return;
                            }
                            var imageList = me.__PARAMS;       
                            var repImage = imageList[0].SRC;
                            var repTitle = imageList[0].FILE_NAME;
                            
                            Ext.apply(me, {
                                items: [{
                                    xtype: 'panel',
                                    layout: {
                                        type :'vbox',
                                        align: 'stretch'
                                    },
                    //				margin : 10,
                                    title: repTitle,
                                    name : 'PHOTO_TITLE',
                                    split: true,
                                    collapsible: true,
                                    region: 'center',
                                    frame: false,
                                    scrollable: 'y',
                                    hideCollapseTool: true,
                                    header: true,  
                                    items: [{
                                        xtype : 'image',
                                        src : repImage,
                                        autoRender : true
                                    }]               
                                },{
                                    xtype: 'panel',
                    //				margin : 10,
                                    padding : 1,
                                    title:'Photo List',
                                    name : 'PHOTO_LIST',
                                    split: true,
                                    collapsible: true,
                                    region: 'east',
                                    frame: false,
                                    scrollable: 'y',
                    //                hideCollapseTool: true,
                                    header: true,
                                    layout: {
                                        type :'vbox',
                                        align: 'stretch'
                                    },
                                    items: [{
                                        xtype: 'dataview',    
                                        itemSelector: 'div.thumb-wrap',
                                        overItemCls: 'overImangeView',
                                        emptyText: 'No images available',
                                        store: Ext.create('Ext.data.Store', {
                                            fields: [],
                                            autoLoad: true,
                                            data: imageList
                                        }),    		        
                                        listeners: {
                                            itemclick: function(cmp, value){                     
                                                var photoPanel = cmp.up('panel').up('panel').down('[name=PHOTO_TITLE]');
                                                photoPanel.setTitle(value.data.FILE_NAME);
                                                photoPanel.items.items[0].setSrc(value.data.SRC);
                                                photoPanel.setScrollable('y');
                                            }
                                        },
                                        tpl: new Ext.XTemplate(
                                                '<tpl for=".">',
                                                '<div style="width: 160px; margin: 10px;" class="thumb-wrap">',
                                                '<li data-tooltip="{FILE_INFO}" class="{[xindex  === 1 ? "selected" : ""]} imagetooltip"><img src="{SRC}" style="height: 150px; width: 160px;"/></li>',
                                                '<br/><span><div style="font-weight: bold; text-align: center;">[{FILE_NAME}]</div></span>',
                                                '</div>',
                                            '</tpl>'
                                        )    			
                                    }]
                                }]		    
                            });
                            me.callParent(arguments);
                        }
                    });    
                }
            });
        </script>
    </head>   
    <body></body>
</html>
```

MY-IMAGEN

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- https://fiddle.sencha.com/#view/editor&fiddle/30pp -->
        <title>FORM SUBMIT</title>
        <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
        <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
            rel = "stylesheet" />
        <script type = "text/javascript" 
            src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
        <script type = "text/javascript">

        Ext.define('MyImage.view.MyImg', {
            extend: 'Ext.Img',

            height: 201,
            renderTo: 'Ext.getBody(),',
            width: 400,
            src: 'https://www.sencha.com/wp-content/uploads/2019/06/productPage-tab-develop-ExtJS-KitchenSink.png',
            title: 'Image Tooltip',

            initComponent: function() {
                var me = this;

                me.callParent(arguments);
            }

        });

        // @require @packageOverrides
        Ext.Loader.setConfig({
            enabled: true
        });


        Ext.application({
            views: [
                'MyImg'
            ],
            name: 'MyImage',

            launch: function() {
                Ext.create('MyImage.view.MyImg', {renderTo: Ext.getBody()});
            }

        });
        </script>
    </head>   
    <body></body>
</html>
```


# 800 Sencha ExtJS y XEditor

### Lista de Recursos de Sencha ExtJS

* Página oficial de Sencha ExtJS: https://www.sencha.com/products/extjs/
* Documentación Ext JS 7.3.1: https://docs.sencha.com/extjs/7.3.1/guides/getting_started/getting_started_with_npm.html
* Documentación Ext JS 6.2.0: https://docs.sencha.com/extjs/6.2.0/index.html
* Ejemplos Ext JS 6.2.0: https://examples.sencha.com/extjs/6.6.0/examples/
* Ejecución de Código: https://fiddle.sencha.com/#view/editor
* TutorialPoins ExtJS: https://www.tutorialspoint.com/extjs/index.htm
* ExtJS-Tutorial.com: https://www.extjs-tutorial.com/ 

#### Libros ExtJS

* PacktPublishing/Ext-JS-6-By-Example: https://github.com/PacktPublishing/Ext-JS-6-By-Example
* Ext JS 6 By Example.pdf: https://github.com/adolfodelarosades/ness-js

#### Videos YouTube Sencha

* Videos Oficiales de Sencha: https://www.youtube.com/c/sencha/videos
* Iniciar un Proyecto de Sencha ExtJS con CMD v7.x: https://www.youtube.com/watch?v=iEeQhheKOeQ
* Sencha Ext JS: https://www.youtube.com/watch?v=cuErKPV3u_0



### Lista de Recursos de XEditor

* Página oficial de XEditor: https://www.xpublisher.com/products/xeditor
* Documentación XEditor: https://documentation.xeditor.com/
* Xeditor 6.6.0 API: https://api.xeditor.com/v6_6/

#### Videos YouTube Xeditor

* Xeditor Presentation https://www.youtube.com/watch?v=zdJNDDnpM9E


