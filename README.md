Para asegurarte de que **Java 17** esté en modo automático en lugar de **Java 21**, sigue estos pasos para modificar correctamente las prioridades y la selección automática:

### 1. Restablecer la selección automática de `update-alternatives`
Primero, puedes restablecer el sistema a la selección automática de Java 17 con este comando:

```bash
sudo update-alternatives --auto java
```

Este comando debe hacer que el sistema seleccione automáticamente la versión con la mayor prioridad.

### 2. Modificar la prioridad de **Java 17**
Si **Java 21** sigue apareciendo como automático, necesitas modificar la prioridad de Java 17 manualmente. Para hacerlo, puedes usar el comando siguiente y asignar a **Java 17** una prioridad más alta que la de **Java 21**.

```bash
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-17-openjdk-amd64/bin/java 3000
```

Esto asigna una prioridad de `3000` a **Java 17**, lo que asegurará que sea seleccionado en modo automático porque su prioridad es mayor que la de **Java 21** (que tiene `2111`).

### 3. Verifica la selección automática
Después de modificar la prioridad, puedes verificar las alternativas con:

```bash
sudo update-alternatives --display java
```

Deberías ver que **Java 17** está configurado como la opción automática.

### 4. Verifica la versión
Confirma que la versión correcta está en uso:

```bash
java -version
```

Si **Java 17** ahora es la versión automática, el problema debería estar resuelto.
