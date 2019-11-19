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

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/constraintLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <ImageView
        android:id="@+id/imgVFoto"
        android:layout_width="116dp"
        android:layout_height="116dp"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/profile" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="Nombre:"
        app:layout_constraintStart_toEndOf="@+id/imgVFoto"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="Apellido:"
        app:layout_constraintStart_toEndOf="@+id/imgVFoto"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="Dirección:"
        app:layout_constraintStart_toEndOf="@+id/imgVFoto"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="Empresa:"
        app:layout_constraintStart_toEndOf="@+id/imgVFoto"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

    <TextView
        android:id="@+id/txtVNombre"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        android:textStyle="bold"
        app:layout_constraintStart_toEndOf="@+id/textView2"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/txtVApellidos"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView3"
        app:layout_constraintTop_toBottomOf="@+id/txtVNombre" />

    <TextView
        android:id="@+id/txtVDir"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView4"
        app:layout_constraintTop_toBottomOf="@+id/txtVApellidos" />

    <TextView
        android:id="@+id/txtVEmpresa"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView5"
        app:layout_constraintTop_toBottomOf="@+id/txtVDir" />

    <TextView
        android:id="@+id/txtVFecha"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imgVFoto" />

    <TextView
        android:id="@+id/textView11"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="Datos de contacto"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/txtVFecha" />

    <TextView
        android:id="@+id/textView12"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="Teléfono 1:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView11" />

    <TextView
        android:id="@+id/textView13"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:text="Teléfono 2:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView12" />

    <TextView
        android:id="@+id/textView14"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:text="Email:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView13" />

    <TextView
        android:id="@+id/txtVTel1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView12"
        app:layout_constraintTop_toBottomOf="@+id/textView11" />

    <TextView
        android:id="@+id/txtVTel2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView13"
        app:layout_constraintTop_toBottomOf="@+id/txtVTel1" />

    <TextView
        android:id="@+id/txtVEmail"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="TextView"
        app:layout_constraintStart_toEndOf="@+id/textView14"
        app:layout_constraintTop_toBottomOf="@+id/txtVTel2" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
</dl>

<dl>
  <a name=Parser><dt>4.  Creamos el parser:</dt></a>
  <dd>Creamos el parser que importara los datos del archivo(json, xml) en el que se almacenara en un array y obtendremos los datos mediante un InputStream.</dd>

```java
    public ContactoParser(Context c){
        this.contactosFile = c.getResources().openRawResource(R.raw.contacts);
    }
```

<dd>Después de crear el constructor y declarar los datos del array y el file empezamos a parsear los campos del archivo.</dd>

```java
    public boolean parse(){
        boolean parsed = false;
        String jsonContactos = null;
        contactos = null;
        try {
            int sizeContactos = contactosFile.available();
            byte[] bufferContactos = new byte[sizeContactos];
            contactosFile.read(bufferContactos);
            contactosFile.close();
            jsonContactos = new String(bufferContactos, "UTF-8");

            JSONTokener tokener = new JSONTokener(jsonContactos);
            JSONArray jsonArray = new JSONArray(tokener);
            contactos = new Contacto[jsonArray.length()];
            for (int i=0; i<jsonArray.length(); i++){
                JSONObject jsonObject = jsonArray.getJSONObject(i);
                int id = jsonObject.getInt("id");
                String nombre = jsonObject.getString("name");
                String apellidos = jsonObject.getString("firstSurname")+" "+jsonObject.getString("secondSurname");
                String fecha = jsonObject.getString("birth");
                String dir = jsonObject.getString("address");
                String tel1 = jsonObject.getString("phone1");
                String tel2 = jsonObject.getString("phone2");
                String email = jsonObject.getString("email");
                String foto = jsonObject.getString("photo");
                String compa = jsonObject.getString("company");
                contactos[i]=new Contacto(id, nombre, apellidos, foto, fecha, compa, email, tel1, tel2, dir);
            }
            parsed=true;
        } catch (IOException e) {
            e.printStackTrace();
        } catch (JSONException e) {
            e.printStackTrace();
        }

        return parsed;
    }
```

</dl>
