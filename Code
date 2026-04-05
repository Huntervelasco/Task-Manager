
import json
import os
archivo = "tareas.json"

def guardar_datos():
    datos = {
        "conta_id": conta_id,
        "tareas": tareas
    }

    with open(archivo, "w", encoding="utf-8") as f:
        json.dump(datos, f, indent=4, ensure_ascii=False)

def cargar_datos():
    global tareas, conta_id

    if not os.path.isfile(archivo):
        return

    with open(archivo, "r", encoding="utf-8") as f:
        datos = json.load(f)

    tareas = datos.get("tareas",[])
    conta_id = datos.get("conta_id", 0)








tareas = [
    {"id": 1,
     "titulo": "Estudiar python",
     "estado": "pendiente"
     }

]  #cada elemento en una lista, es un diccionario
conta_id = 1

def mostrar_tareas():
    if not tareas:
        print("No hay tareas por el momento")
        return  #funciona como freno, para que lo siguiente de la funcion no sea ejecutado, solo si la validacion se cumple

    for tarea in tareas:   #“Para cada elemento dentro de la lista tareas, guárdalo temporalmente en la variable tarea.
        print(f"[{tarea['id']}]  {tarea['titulo']} - {tarea['estado']}")


def agregar_tareas():
    title = input("Nombre de la nueva tarea: ")
    global conta_id
    if not title:
        print("respuesta invalida")
        return

    for tarea in tareas:
        if tarea['titulo'] == title:
            print("esa tarea ya existe")
            return

    estado = input("Estado: ")
    conta_id += 1
    tareas.append({
        "id": conta_id,
        "titulo": title,
        "estado": estado
        })
    guardar_datos()


def marcar_completada():
    option_2 = input("deseas ingresar el (1) titulo o el (2) numero de la tarea?: ")
    if not option_2:
        print("respuesta invalida")
        return

    if option_2 == "1":
        name_task = input("dame el nombre de la tarea: ")


        for tarea in tareas:
            if tarea['titulo'] == name_task:
                if tarea['estado'] == 'completado':
                    print("la tarea ya estaba completada")
                    return

                tarea['estado'] = "completado"
                print("tarea marcada como completada")
                guardar_datos()
                return

        print("no se encontro la tarea")

    elif option_2 == "2":
        num_task = input("dame el numero de la tarea: ")
        try:
            num_task = int(num_task)
            if num_task < 1:
                print("respuesta invalida")
                return

        except ValueError:
            print("respuesta invalida")
            return



        for tarea in tareas:
            if tarea['id'] == num_task:

                if tarea['estado'] == 'completado':
                    print("la tarea ya estaba completada")
                    return
                else:
                    tarea['estado'] = "completado"
                    print("tarea marcada como completada")
                    guardar_datos()
                    return

        print("no se encontro la tarea")
    else:
        print("respuesta invalida")
        return


def editar_tarea():
    option_3 = input("Escribe '1' para ingresar el nombre de la tarea\nEscribe '2' para ingresar el numero de la tarea")

    if not option_3:
        print("Respuesta invalida")
        return
    try:
        option_3 = int(option_3)
        if option_3 < 1 or option_3 > 2:
            print("respuesta invalida")
            return
    except ValueError:
        print("Respuesta invalida")

    if option_3 == 1:  #falta la OPCION 2, ingresar el numero de la tarea
        name_task = input("Dame el nombre de la tarea: ")
        for tarea in tareas:
            if tarea['titulo'] == name_task:
                option_31 = input("Quieres cambiar \n(1) el nombre de la tarea\n(2)el estado:\n")
                if not option_31:
                    print("respuesta invalida")
                    return
                try:
                    option_31 = int(option_31)
                    if option_31 < 1 or option_31 > 2:
                        print("respuesta invalida")
                        return
                except ValueError:
                    print("respuesta invalida")
                    return
                if option_31 == 1:
                    new_name = input("Dame el nombre que le quieres dar: ")
                    if not new_name:
                        print("respuesta invalida")
                        return
                    tarea['titulo'] = new_name
                    print(f"Tarea cambiada, el nuevo nombre es: {new_name}")
                    guardar_datos()
                    return
                elif option_31 == 2:
                    new_estado = input("Dame el nuevo estado de la tarea: ")
                    if not new_estado:
                        print("respuesta invalida")
                        return
                    tarea['estado'] = new_estado
                    print(f"el estado ha sido cambiado a {new_estado}")
                    guardar_datos()
                    return
                else:
                    print("respuesta invalida")
                    return

        print("No se encontro la tarea")

def eliminar_tarea():
    global conta_id
    option_4 = input("Para eliminar dame\n(1)el nombre\n(2)el numero")
    if not option_4:
        print("respuesta invalida")
        return
    try:
        option_4 = int(option_4)
        if option_4 < 1 or option_4 > 2:
            print("respuesta invalida")
            return
    except ValueError:
        print("respuesta invalida")
        return

    if option_4 == 1:
        name_task = input("dame el nombre de la tarea: ")

        if not name_task:
            print("respuesta invalida")
            return
        for tarea in tareas:
            if tarea['titulo'] == name_task:
                tareas.remove(tarea)

                print("tarea eliminada")
                guardar_datos()
                return
        print("no se encontro la tarea")

    elif option_4 == 2:
        num_task = input("dame el numero de la tarea: ")

        if not num_task:
            print("respuesta invalida")
            return
        try:
            num_task = int(num_task)
            if num_task < 1:
                print("respuesta invalida")
                return
        except ValueError:
            print("respuesta invalida")
            return
        for tarea in tareas:
            if tarea['id'] == num_task:

                tareas.remove(tarea)
                print("tarea eliminada")
                guardar_datos()
                return

        print("no se encontro la tarea")

def salir():
    print("gracias por usar el programa")
    guardar_datos()




cargar_datos()
while True:
    print("\n1. Ver tareas")
    print("2. Agregar tareas")
    print("3. Marcar completada")
    print("4. Editar tarea")
    print("5. Eliminar tarea")
    print("6. Salir")

    option_1 = input("Que opcion eliges: ")

    try:
        option_1 = int(option_1)
        if option_1 < 1 or option_1 > 6:
            print("Opcion invalida")
            continue

    except ValueError:
        print("Opcion invalida, debe ser un numero.")
        continue

    if option_1 == 1:
        mostrar_tareas()

    elif option_1 == 2:
        agregar_tareas()

    elif option_1 == 3:
        marcar_completada()
    elif option_1 == 4:
        editar_tarea()
    elif option_1 == 5:
        eliminar_tarea()
    elif option_1 == 6:
        salir()
        break




