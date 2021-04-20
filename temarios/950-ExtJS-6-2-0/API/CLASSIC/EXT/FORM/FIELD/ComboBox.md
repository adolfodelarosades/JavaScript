# `Ext.form.field.ComboBox`

Un control de cuadro combinado con soporte para autocompletar, carga remota y muchas otras características.

Un ComboBox es como una combinación de un campo <input> de texto HTML tradicional y un campo <select>; el usuario puede escribir libremente en el campo y / o elegir valores de una lista de selección desplegable. El usuario puede ingresar cualquier valor por defecto, incluso si no aparece en la lista de selección; para evitar valores de forma libre y restringirlos a elementos de la lista, establezca forceSelection en true.

Las opciones de la lista de selección se completan desde cualquier Ext.data.Store, incluidas las tiendas remotas. Los elementos de datos en la tienda se asignan al texto mostrado de cada opción y al valor de respaldo a través de las configuraciones valueField y displayField, respectivamente.

Si su tienda no es remota, es decir, depende solo de los datos locales y se carga por adelantado, debe asegurarse de establecer queryMode en 'local', ya que esto mejorará la capacidad de respuesta del usuario.
