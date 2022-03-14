# **Proyecto de Programación** #
``` python 
consumo_energia = {
    'Coca Codo Sinclair': {
        'Quito': { 'consumos':(400, 432, 400, 432, 420, 432, 460, 432, 400, 432, 300 , 213),'tarifa': 65},
        'Guayaquil': { 'consumos': (120, 55, 32, 120, 75, 32, 150, 55, 32, 120, 97, 32),'tarifa': 84},
    },
    'Sopladora': {
        'Guayaquil':{ 'consumos': (310, 220, 321, 310, 220, 321, 310, 220, 321, 310, 220, 321),'tarifa':55},
        'Quito': { 'consumos': (400, 432, 587, 400, 432, 587, 400, 432, 587, 400, 432, 587),'tarifa': 79},
        'Loja': { 'consumos': (50, 32, 32, 50, 32, 32, 50, 32, 32, 50, 32, 32),'tarifa': 32},
    },
}

plantas = {
    'Quito': ('Coca Codo Sinclair', 'Sopladora'),
    'Guayaquil': ('Coca Codo Sinclair', 'Sopladora'),
    'Loja': ('Sopladora')
}

inf = {
    'costa': ('Guayaquil', 'Manta'),
    'sierra': ('Quito', 'Ambato', 'Loja'),
    'oriente': ('Tena', 'Nueva Loja')
}

def menu_principal ():
    print('<1> MWh planta/ciudad\n<2> MWh plantas/ciudad\n<3> Dinero recaudado por región\n<4> Terminar programa')

def primer_menu ():
    pt = str(input('Ingrese el nombre de la planta(ingresar en mayúsculas): '))
    cd = str(input('Ingrese el nombre de la ciudad(ingresar en mayúsculas): '))

    if pt == 'COCA CODO SINCLAIR' and cd =='QUITO':
    #C-Quito
        tarifa_coca_quito = consumo_energia['Coca Codo Sinclair']['Quito']['tarifa']

        print('Consumo total:', sum(consumo_energia['Coca Codo Sinclair']['Quito']['consumos']),'MWh')

    elif pt == 'COCA CODO SINCLAIR' and cd == 'GUAYAQUIL':
        #C-Guayquil
        tarifa_coca_guayaquil = consumo_energia['Coca Codo Sinclair']['Guayaquil']['tarifa']

        print('Consumo total:', sum(consumo_energia['Coca Codo Sinclair']['Guayaquil']['consumos']),'MWh')

    elif pt == 'SOPLADORA' and cd == 'GUAYAQUIL':
    #S-Guayaquil
        tarifa_sopladora_guayaquil = consumo_energia['Sopladora']['Guayaquil']['tarifa']

        print('Consumo total:', sum(consumo_energia['Sopladora']['Guayaquil']['consumos']),'MWh')

    elif pt == 'SOPLADORA' and cd == 'QUITO':
    #S-Quito
        tarifa_sopladora_quito = consumo_energia['Sopladora']['Quito']['tarifa']
        
        print('Consumo total:', sum(consumo_energia['Sopladora']['Quito']['consumos']),'MWh')

    elif pt == 'SOPLADORA' and cd == 'LOJA':
    #S-Loja
        tarifa_sopladora_loja = consumo_energia['Sopladora']['Loja']['tarifa']

        print('Consumo total:', sum(consumo_energia['Sopladora']['Loja']['consumos']),'MWh')

    else:
        print('¡DATOS ERRONEOS!\nINGRESE NUEVAMENTE LOS DATOS DE LA PLANTA Y LA CIUDAD')

def sdo_menu ():
    cd = str(input('Ingrese el nombre de la ciudad(ingresar en mayúsculas): '))
    if cd == 'QUITO':
        print('Las plantas que producen energia en esta ciudad son', plantas['Quito'])
        print('COCA CODO SINCLAIR:', sum(consumo_energia['Coca Codo Sinclair']['Quito']['consumos']),'MWh')
        print('SOPLADORA:', sum(consumo_energia['Sopladora']['Quito']['consumos']),'MWh')

    elif cd == 'GUAYAQUIL':
        print('Las plantas que producen energia en esta ciudad son', plantas['Guayaquil'])
        print('COCA CODO SINCLAIR:', sum(consumo_energia['Coca Codo Sinclair']['Guayaquil']['consumos']),'MWh')
        print('SOPLADORA:', sum(consumo_energia['Sopladora']['Guayaquil']['consumos']),'MWh')

    elif cd == 'LOJA':
        print('SOPLADORA:', sum(consumo_energia['Sopladora']['Loja']['consumos']),'MWh')
    else:
        print('¡La ciudad que desea consultar no recibe energía!')

def tr_menu ():
    rg = str(input('Ingrese el nombre de una region(ingresar en mayúsculas): '))
    if rg == 'SIERRA':
        q_c_a = sum(consumo_energia['Coca Codo Sinclair']['Quito']['consumos'])
        q_c_b = sum(consumo_energia['Sopladora']['Quito']['consumos'])
        q_t_a = consumo_energia['Coca Codo Sinclair']['Quito']['tarifa']
        q_t_b = consumo_energia['Sopladora']['Quito']['tarifa']

        l_c_a = sum(consumo_energia['Sopladora']['Loja']['consumos'])
        l_t_a = consumo_energia['Sopladora']['Loja']['tarifa']
        print('Los ingresos de la región Sierra:', '$',((q_c_a*q_t_a) + (q_c_b*q_t_b)) + (l_c_a*l_t_a))
    elif rg == 'COSTA':
        g_c_a = sum(consumo_energia['Coca Codo Sinclair']['Guayaquil']['consumos'])
        g_c_b = sum(consumo_energia['Sopladora']['Guayaquil']['consumos'])
        g_t_a = consumo_energia['Coca Codo Sinclair']['Guayaquil']['tarifa']
        g_t_b = consumo_energia['Sopladora']['Guayaquil']['tarifa']
        print('Los ingresos de la región Costa:', '$',((g_c_a*g_t_a) + (g_c_b*g_t_b)))
    elif rg == 'ORIENTE':
        print('¡La región no tiene registros!')
    else:
        print('¡Error!')


op = -1
while op != 0:
    menu_principal()
    n1 = int(input('Ingrese una opción: '))
    while n1 == 1:
        primer_menu ()
        print('¡Regresando al menú principal!')
        break
    while n1 == 2:
        sdo_menu ()
        print('¡Regresando al menú principal!')
        break
    while n1 == 3:
        tr_menu ()
        print('¡Regresando al menú principal!')
        break
    while n1 == 4:
        print('¡Finaliza el programa!')
        print ('.....................................................')
        print ('.....................................................')
        print ('.....................................................')
        print ('.....................................................')
        print ('.....................................................')
        print ('REALIZADO POR------ NATHAN SANI ')
        print ('Gracias')
        quit ()
``` 


