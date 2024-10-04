Que es un test unitario ?

Un test unitario en Angular con Karma es una prueba automatizada que verifica el comportamiento de una unidad específica de código, como un componente, servicio o directiva, para asegurar que funciona correctamente de forma aislada.

Cómo funciona:
Cuando escribes un test unitario en Angular, utilizas Jasmine (framework de testing) para definir los casos de prueba, y Karma ejecuta esos tests en un entorno de navegador simulado. Los resultados de los tests son mostrados en la consola.

Ejemplo sencillo de un test unitario en Angular:
Supongamos que tienes un componente llamado MiComponente, y deseas probar que su método sumar() funciona correctamente.

// mi-componente.component.ts
export class MiComponente {
  sumar(a: number, b: number): number {
    return a + b;
  }
}

El test unitario podría ser algo como:

// mi-componente.component.spec.ts
import { MiComponente } from './mi-componente.component';

describe('MiComponente', () => {
  let componente: MiComponente;

  beforeEach(() => {
    componente = new MiComponente();
  });

  it('debería sumar dos números correctamente', () => {
    const resultado = componente.sumar(2, 3);
    expect(resultado).toBe(5);
  });
});


Proceso de ejecución:
Escribes los tests usando Jasmine.
Karma ejecuta estos tests en el navegador que configures (Chrome, Firefox, etc.).
Los resultados se muestran en la consola o interfaz de Karma, indicando si el test ha pasado o fallado.
