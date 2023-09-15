```mermaid
classDiagram
  class Usuario {
    +String correoElectronico
    +String contrasena
    +Cuenta[] cuentas
    +Categoria[] categorias
    +PanelDeControl panelDeControl
    +Registro()
    +InicioDeSesion()
    +AccederPanelDeControl()
    +GestionarCuentas()
    +GestionarMovimientos()
    +CategorizarMovimientos()
    +TraspasarDinero()
    +ConsultarMovimientos()
  }

  class Cuenta {
    +String nombre
    +double saldoInicial
    +double saldoActual
    +Usuario propietario
    +Movimiento[] movimientos
    +CrearMovimiento()
    +ActualizarSaldo()
    +TransferirDinero()
  }

  class Categoria {
    +String nombre
    +Usuario propietario
    +Movimiento[] movimientos
  }

  class Movimiento {
    +String descripcion
    +double monto
    +Date fecha
    +Categoria categoria
    +Cuenta cuenta
  }

  class PanelDeControl {
    +double saldoTotal
    +double[] saldoPorCuenta
    +double balanceIngresos
    +double balanceGastos
    +Usuario propietario
  }

  Usuario --|> Cuenta : tiene
  Usuario --|> Categoria : tiene
  Usuario --> PanelDeControl : accede a
  Categoria --|> Movimiento : contiene
  Cuenta --|> Movimiento : registra
  Categoria --|> Movimiento : contiene
  Cuenta *--* Cuenta : permite transferir dinero a
```
