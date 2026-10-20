# Práctica 14 - La tienda contra su API

Conecté la tienda de la práctica anterior con el backend. Ya no usa el arreglo local, los productos vienen de la API y el formulario de pago manda el carrito y devuelve un folio.

## Preguntas

**¿Por qué en la pestaña Red salen dos peticiones al cargar?**
Por el StrictMode de React en desarrollo. Desmonta y vuelve a montar el componente una vez para detectar errores, por eso el efecto corre dos veces.

**¿Qué pasa si quitas el arreglo de dependencias del efecto?**
El efecto corre después de cada render. Como actualiza el estado, genera otro render, que vuelve a correr el efecto, y así infinitamente. En la pestaña Red se ve un loop de peticiones.

**¿Qué hace `e.preventDefault()` y qué pasa si lo quitas?**
Cancela el envío nativo del formulario que recargaría la página. Sin él, al presionar Pagar la página se recarga y React pierde todo el estado.

## Lo que agregué

- `src/api/cliente.ts` — instancia de Axios con el baseURL y timeout
- `src/servicios/productos.service.ts` — hace el GET y saca el `data` del sobre
- `src/servicios/pedidos.service.ts` — hace el POST y maneja los errores 400 y 409
- `src/hooks/useProductos.ts` — maneja los estados cargando/error/productos
- `src/componentes/Cargando.tsx` y `MensajeError.tsx` — copiados del código base
- `src/componentes/FormularioPago.tsx` — formulario controlado con validaciones

Los componentes de la práctica anterior no se tocaron (`git diff` sin cambios en ellos).
