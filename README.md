## GUIDELINES ANDROID ##

# Pull Requests

  - Minimo dos personas en el pull request (las dos deben aprobar).
  
# Dimens

- Siempre se debe usar los dimens por defecto para tamaño de fuentes.
- En lo posible usar los "spacing" por defecto para margin, padding, etc.

# Strings
Se debe separar las cadenas de texto por pantalla y nombrarlas de la siguiente manera:

```xml
<string name="login.title">Inicio de sesion.</string>

<string name="profile.logout">Cerrar sesion.</string>
```
Ningun String puede estar totalmente en mayuscula, usar textAllCaps para eso.

No importa que se repita un texto, si son de diferentes pantallas se deben crear ambos recursos.


# Colors
Todos los colores deben estar dentro de `colors.xml` con el formato RGBA. La idea es mantener simple la paleta de colores y no repetir valores con nombres diferentes.

No hacer esto:

```xml
<resources>
    <color name="one_color">#2A91BD</color>
    <color name="the_same_color">#2A91BD</color>
</resources>
```

Mejor, hacer esto:

```xml
<resources>
  <!-- grayscale -->
  <color name="gray">#939393</color>
  <color name="gray_light">#DBDBDB</color>
  <color name="gray_dark">#5F5F5F</color>
 
  <!-- basic colors -->
  <color name="white">#FFFFFF</color>
  <color name="black">#323232</color>
  <color name="green">#27D34D</color>
  <color name="blue">#2A91BD</color>
  <color name="orange">#FF9D2F</color>
  <color name="red">#FF432F</color>

  <!-- brand colors -->
  <color name="red_brand_primary">#ea2127</color>
  <color name="red_brand_secondary">#8c0a0e</color>
  <color name="red_brand_dark">#d0534f</color>
</resources>
```

# Nombre layouts
El nombre de cada archivo que se use como layout debe ser nombrado de la siguente manera:

##### - fragment_profile.xml
##### - activity_splash.xml

# Nombre de Clases
Si una clase hereda de un componente Android, el nombre debe finalizar con el nombre del componente, por ejemplo:
* `TestActivity`
* `TestFragment`
* `TestService`
* `TestDialogFragment`

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `MapActivity`          | `activity_map.xml`            |
| Fragment         | `ContactUsFragment`    | `fragment_contact_us.xml`     |
| AdapterView item | ---                    | `item_address.xml`            |
| PartialLayout    | ---                    | `layout_home_market.xml`      |

# Jerarquia de Vistas
Evitar crear jerarquias profundas de vistas usando, por ejemplo, muchos LinearLayouts anidados:

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    >

    <RelativeLayout
        ...
        >

        <LinearLayout
            ...
            >

            <LinearLayout
                ...
                >

                <LinearLayout
                    ...
                    >
                </LinearLayout>

            </LinearLayout>

        </LinearLayout>

    </RelativeLayout>

</LinearLayout>
```

Es mejor tratar de optimizar usando RelativeLayouts o la etiqueta [`<merge>`](http://stackoverflow.com/questions/8834898/what-is-the-purpose-of-androids-merge-tag-in-xml-layouts).

# Id XML

Todos los ids que se usen para hacer referencia en la una actividad , fragmento ó vista deben ser nombrados de la siguente manera:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    android:id="@+id/rlSplash"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/splash"
    android:orientation="vertical">

    <ImageView
        android:id="@+id/ivSplash"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:background="@drawable/ic_splash_prueba"
        android:contentDescription="@string/app_name"
        android:visibility="invisible"/>

    <ImageView
        android:id="@+id/ivSplashStorekeeper"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="@dimen/spacing_large"
        android:background="@drawable/ic_splash_prueba"        
        android:contentDescription="@string/app_name"/>

</RelativeLayout>
```


# Drawables

En todos los pull request deben ir las imágenes adaptadas para las densidades definidas.
- mdpi
- xxhdpi
- xxxhdpi

# Variables en actividades, fragments ó vistas

- Todas las variables deben ir ordenadas por el tipo de dato.
- Todas las variables publicas y estáticas debe ir al principio del archivos y en mayúscula.

```Java
public class TestFragment extends BaseFragment {

    public static String TAG = TestFragment.getClass().getSimpleName();

    private TextView tvMessage;
    private TextView tvCountry;
    
    private RelativeLayout rlUnRegisteredUser;

    private Button btnCancel;
    private Button btnOk;

    private User user;

    private int count;
    private int aux;

    private boolean flag;
    
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        return inflater.inflate(R.layout.fragment_test, container, false);
    }
}
```
# No agrupar las variables del mismo tipo

Mal

```Java
private String value, name, lastName; 
```

Bien

```Java
private String value; 
private String name;
private String lastName;
```

# Nombres de metodos

Los nombres de metodos deben explicar claramente que hacen y no ser genericos.

# Nombres de variables

Deben ser claros para poder identificar el tipo de dato y la información que guardan

# Anotaciones

Antes de una anotacion siempre debe ir un salto de linea para evitar que se agrupen un monton de anotaciones y declaraciones de variables

# Styles

Para manejar los estilos de fuente, tamaño y color, se trabajaria de la siguiente manera:

```

    <style name="TextNormal">
        <item name="android:textSize">@dimen/font_normal</item>
    </style>

    <style name="TextNormal.White" parent="TextNormal">
        <item name="android:textColor">@color/white</item>
    </style>

    <style name="TextNormal.Black" parent="TextNormal">
        <item name="android:textColor">@color/black</item>
    </style>

    <style name="TextNormal.White.Bold" parent="TextNormal.White">
        <item name="android:textStyle">bold</item>
    </style>

    <style name="TextNormal.Black.Bold" parent="TextNormal.Black">
        <item name="android:textStyle">bold</item>
    </style>

```
