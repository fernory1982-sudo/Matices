# Nombre del estudiante: Ferney [Morales Muñoz]
# Grupo: [213022_802]
# Programa: [conjunto de problema 10,arreglos (matrices)]
# Código Fuente:realiza las operaciones siguientes:
# Universidad Nacional Abierta y a Distancia - UNAD
# Curso: Fundamentos de Programación
# Fase 3 – Estructuras repetitivas y arreglos problema 10

#4 empleados
#3 días
#Matriz A = Tareas completadas por cada empleado por día (enteros mayor a 0)
#Matriz B = Tiempo promedio por tarea (en minutos) por cada empleado por día (enteros mayor a 0)
#Matriz C = A × B (producto elemento a elemento)
#Mostrar la matriz C completa
#Empleado que acumuló más tiempo total en los 3 días
#Día con mayor tiempo total trabajado por todos los empleados

# PROBLEMA 10 - Análisis de productividad

print("ANÁLISIS DE PRODUCTIVIDAD DE EQUIPO")

# Dimensiones
NUM_EMPLEADOS = 4
NUM_DIAS = 3

# 1. INGRESO DE DATOS - Matriz A (Tareas completadas)

print("Ingrese la cantidad de tareas completadas por cada empleado en cada día:\n")

A = []
for i in range(NUM_EMPLEADOS):
    fila = []
    print(f"Empleado {i+1}:")
    for j in range(NUM_DIAS):
        while True:
            try:
                tareas = int(input(f"   Día {j+1}: "))
                if tareas > 0:
                    fila.append(tareas)
                    break
                else:
                    print("   Error: Debe ser un número mayor que 0.")
            except ValueError:
                print("   Error: Ingrese un número entero válido.")
    A.append(fila)

# 2. INGRESO DE DATOS - Matriz B (Tiempo promedio por tarea)
print("\nIngrese el tiempo promedio (en minutos) que cada empleado tarda por tarea:\n")

B = []
for i in range(NUM_EMPLEADOS):
    fila = []
    print(f"Empleado {i+1}:")
    for j in range(NUM_DIAS):
        while True:
            try:
                tiempo = int(input(f"   Día {j+1}: "))
                if tiempo > 0:
                    fila.append(tiempo)
                    break
                else:
                    print("   Error: Debe ser un número mayor que 0.")
            except ValueError:
                print("   Error: Ingrese un número entero válido.")
    B.append(fila)

# 3. CÁLCULO DE LA MATRIZ C (Tiempo total trabajado)

C = []
for i in range(NUM_EMPLEADOS):
    fila = []
    for j in range(NUM_DIAS):
        tiempo_total = A[i][j] * B[i][j]   # Producto elemento a elemento
        fila.append(tiempo_total)
    C.append(fila)

# 4. MOSTRAR RESULTADOS

print("\n" + "="*60)
print("MATRIZ C - TIEMPO TOTAL TRABAJADO (en minutos)")
print("="*60)

# Mostrar matriz C con formato bonito
print("          Día 1     Día 2     Día 3")
print("-" * 60)
for i in range(NUM_EMPLEADOS):
    print(f"Empleado {i+1}:  {C[i][0]:8}  {C[i][1]:8}  {C[i][2]:8}")

print("="*60)

# 5. Empleado con mayor tiempo total acumulado

total_por_empleado = [sum(fila) for fila in C]
empleado_max = total_por_empleado.index(max(total_por_empleado)) + 1
tiempo_max = max(total_por_empleado)

print(f"\nEmpleado con mayor tiempo de trabajo acumulado: **Empleado {empleado_max}**")
print(f"Tiempo total: {tiempo_max} minutos")


# 6. Día con mayor tiempo total (sumando todos los empleados)

total_por_dia = [0] * NUM_DIAS
for j in range(NUM_DIAS):
    for i in range(NUM_EMPLEADOS):
        total_por_dia[j] += C[i][j]

dia_max = total_por_dia.index(max(total_por_dia)) + 1
tiempo_dia_max = max(total_por_dia)

print(f"Día con mayor tiempo total trabajado por el equipo: **Día {dia_max}**")
print(f"Tiempo total del día: {tiempo_dia_max} minutos")
print("="*60)
