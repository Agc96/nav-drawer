# Navigator Drawer (sidebar)
Ejemplo para un navigation drawer (sidebar) en Android dentro de un proyecto de Android Studio.

## Indicaciones
Se han agregado un par de cosas cosas respecto a la presentación original:

1. Ahora tenemos un sidebar con **dos grupos** claramente definidos y con un **separador**. Esto se logra colocando identificadores únicos a los items y grupos que son hijos del menú principal:
```XML
  <menu ...>
    <group android:id="@+id/nav_multimedia">
      ...
    </group>
    <item android:id="@+id/nav_options">
      ...
    </item>
  </menu>
```

2. Al segundo grupo también se le añadió un **label**, esto se hace colocando un item para representar al grupo entero dentro del menú principal (con un id, para activar el separador, y cuyo título representará al label del grupo), y dentro del item del label se coloca un **submenú** (el tag sigue siendo `<menu>`) con los items del grupo dentro de dicho submenú.
```XML
  <item
      android:id="@+id/nav_options"
      android:title="Título del label">
    <menu>
      <group android:checkableBehavior="single">
        <item ... />
        <item ... />
        <item ... />
      </group>
    </menu>
  </item>
```
Los items en realidad no están colocados directamente dentro del submenú, sino que están dentro de un **grupo** con la propiedad `android:checkableBehavior="single"`, esto es porque por defecto los items del submenú aparecen como no clickeables después de hacer clic (visualmente, porque aún se ejecutan las acciones que definimos en el `OnNavigationItemSelectedListener`), y con esta propiedad podemos resaltar cualquiera de los items dentro del grupo cuando se hagan clic en estos.

