### Ciclo con un for
~~~
Sub evento()
    si_abona = 0
    no_abona = 0
    abono_10000 = 0
    total_abonado = 0
    For i = 1 To 3
        pregunta = InputBox("¿Va a abonar? " & i)
        If pregunta = "si" Then
            si_abono = si_abono + 1
            dinero = Int(InputBox("¿Cuánto va a abonar?"))
            total_abonado = total_abonado + dinero
            If dinero >= 10000 Then
                abono_10000 = abono_10000 + 1
            End If
        Else
            no_abono = no_abono + 1
        End If
    Next i
    promedio = total_abonado / si_abono
    MsgBox "Donaron " & si_abono & " personas"
    MsgBox "No donaron " & no_abono & " personas"
    MsgBox "Donaron más de 10000 " & abono_10000 & " personas"
    MsgBox "El total abonado fue " & total_abonado
    MsgBox "El promedio de los estudiantes que donaron es " & promedio
End Sub
~~~

### Ciclo con un while
~~~
Sub ejercicio()

    dinero_total = 0
    While dinero_total < 3000000
        pregunta = Int(InputBox("Cuánto va a abonar"))
        If pregunta > 0 Then
            si_abona = si_abona + 1
            If pregunta >= 10000 Then
                abono_10000 = abono_10000 + 1
            End If
            dinero_total = dinero_total + pregunta
        Else
            no_abona = no_abona + 1
        End If
    Wend
    promedio = dinero_total / si_abona
    MsgBox "Donaron (" & si_abona & ") personas"
    MsgBox "No donaron (" & no_abona & ") personas"
    MsgBox "Donaron más de 10000 (" & abono_10000 & ") personas"
    MsgBox "El total abonado es " & dinero_total
    MsgBox "El promedio de los estudiantes que donaron es " & promedio
    
End Sub
~~~

### Ejemplo de formulario
~~~
Private Sub buscar_Click()
    
    x = 3
    sw = True
    busqueda = InputBox("Digite el número de placa")
    While sw
        If datos.Cells(x, 1) = busqueda Then
            placa.Text = datos.Cells(x, 1)
            propietario.Text = datos.Cells(x, 2)
            marca.Text = datos.Cells(x, 3)
            modelo.Text = datos.Cells(x, 4)
            año.Text = datos.Cells(x, 5)
            editar.Enabled = True
            eliminar.Enabled = True
            datos.Cells(1, 7) = x
            sw = False
        End If
        If datos.Cells(x, 1) = Empty Then
            MsgBox "Su placa no está registrada"
            sw = False
        End If
        x = x + 1
    Wend
    
End Sub

Private Sub editar_Click()

    propietario.Enabled = True
    marca.Enabled = True
    modelo.Enabled = True
    año.Enabled = True
    guardar.Enabled = True
    buscar.Enabled = False
    contador = datos.Cells(1, 7)
            
End Sub

Private Sub eliminar_Click()

    confirmacion = MsgBox("¿Desea borrar?", vbQuestion + vbYesNo + vbDefaultButton2, "Mensaje")
    If confirmacion = vbYes Then
        contador = datos.Cells(1, 7)
        datos.Rows(contador).EntireRow.Delete
        datos.Cells(1, 6) = datos.Cells(1, 6) - 1
        datos.Cells(1, 7) = datos.Cells(1, 6)
        placa.Text = Empty
        propietario.Text = Empty
        marca.Text = Empty
        modelo.Text = Empty
        año.Text = Empty
    End If
    
End Sub

Private Sub guardar_Click()

    i = datos.Cells(1, 7)
    datos.Cells(i, 1) = placa.Text
    datos.Cells(i, 2) = propietario.Text
    datos.Cells(i, 3) = marca.Text
    datos.Cells(i, 4) = modelo.Text
    datos.Cells(i, 5) = año.Text
    nuevo.Enabled = True
    guardar.Enabled = False
    placa.Enabled = False
    propietario.Enabled = False
    marca.Enabled = False
    modelo.Enabled = False
    año.Enabled = False
    buscar.Enabled = True
    
End Sub

Private Sub nuevo_Click()

    nuevo.Enabled = True
    placa.Enabled = True
    propietario.Enabled = True
    marca.Enabled = True
    modelo.Enabled = True
    año.Enabled = True
    placa.SetFocus
    datos.Cells(1, 6) = datos.Cells(1, 6) + 1
    datos.Cells(1, 7) = datos.Cells(1, 6)
    nuevo.Enabled = False
    guardar.Enabled = True
    placa.Text = Empty
    propietario.Text = Empty
    marca.Text = Empty
    modelo.Text = Empty
    año.Text = Empty
    buscar.Enabled = False
    
End Sub
~~~
