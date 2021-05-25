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


