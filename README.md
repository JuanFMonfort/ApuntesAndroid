V-11/11/19
# Guiá de pasos Creación de Aplicación Android.

**<a href=#Extern>1. Documentos externos.</a>**  
----
**<a href=#Datos>2. Modelo de datos.</a>**  
----
**<a href=#LayoutsFrag>3. Layouts de los fragments.</a>**  
----
**<a href=#Parser>4. Perser.</a>**  
----
**<a href=#Listener>5. Listener</a>**  
----
**<a href=#Adaptadores>6. Adaptadores</a>**  
----
**<a href=#Fragments>7. Fragments</a>**  
----
**<a href=#MainActivity>8. MainActivity</a>**  
----
**<a href=#Layouts>9. Layouts</a>**  
----
**<a href=#Manifest>10. Manifest</a>**  
----

<dl>
  <a name=Extern><dt>1. Importacion de los Documentos externos:</dt></a>
  <dd>Para los archivos de imagen(png, jpg), se guardaran dentro de la carpeta “./res/drawable(v24)”. 
    
   Para los archivos de datos(xml, json), se guardaran dentro de la carpeta “./res/raw”, que se creara manualmente si no esta ya creada. </dd>
</dl>

<dl>
  <a name=Datos><dt>2.  Creación de los modelos de datos:</dt></a>
  <dd>Crearemos los modelos de datos en relación con los documentos que hemos importado anteriormente(si hay), y implementamos en la clase Serializable. </dd>
</dl>

<dl>
  <a name=LayoutsFrag><dt>3.  Creamos los layouts de los fragments:</dt></a>
  <dd>Dependiendo de como sea la aplicación, si hay una lista principal creamos un listitem de el modelo que queramos listar, en el que introduciremos los datos que queramos mostrar en las opciones de la lista.</dd>
  
```xml
  <?xml version="1.0" encoding="utf-8"?>
  <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/txtVNum"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/txtVNom" />

    <TextView
        android:id="@+id/txtVNom"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:text="TextView"
        android:textSize="18sp"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
<dd>Crearemos los fragments  uno para la lista y otro para el detalle, en la opción de la lista introduciremos el listView  que le daremos el nombre lstListado, en la opción del detalle introduciremos los campos que queramos que se muestren cuando seleccionemos un campo del fragment_listado.
</dd>
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ListView
        android:id="@+id/lstListado"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</LinearLayout>
```
</dl>
