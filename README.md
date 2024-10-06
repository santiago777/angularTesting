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

Anatomia de un test
La anatomía de un test en Angular utilizando Jasmine (para definir los tests) y Karma (para ejecutarlos) sigue una estructura básica que te permite organizar y escribir pruebas de manera clara. Veamos los componentes clave de un test típico:

1. describe(): El bloque de descripción
Este bloque agrupa un conjunto de pruebas relacionadas. Suele representar el componente, servicio o funcionalidad que se está probando.

Sintaxis:

describe('Nombre de la unidad a probar', () => {
  // Aquí van los tests
});

Ejemplo:
describe('MiComponente', () => {
  // tests para MiComponente
});

2. it(): El bloque de prueba
Dentro de un bloque describe(), definimos los casos de prueba individuales con el bloque it(). Cada it() representa un test específico que verifica una funcionalidad o comportamiento.

Sintaxis:
it('debería hacer algo específico', () => {
  // Lógica del test
});


Ejemplo:
it('debería sumar dos números', () => {
  const resultado = componente.sumar(1, 2);
  expect(resultado).toBe(3);
});


3. beforeEach(): Configuración previa
Este bloque es opcional y se usa para preparar el entorno antes de ejecutar cada test. Es útil para inicializar variables o crear instancias de componentes/servicios.

Sintaxis:
beforeEach(() => {
  // Configuración previa al test
});


Ejemplo:

let componente: MiComponente;

beforeEach(() => {
  componente = new MiComponente();
});


4. Expectativa (expect())
El bloque expect() es donde se realizan las verificaciones. Aquí es donde comparas los resultados reales con los esperados utilizando matchers (como .toBe(), .toEqual(), .toThrow(), etc.).
Sintaxis:

expect(valorReal).toBe(valorEsperado);

Ejemplo:
expect(componente.sumar(1, 2)).toBe(3);



Ejemplo completo de anatomía de un test:

import { MiComponente } from './mi-componente.component';

describe('MiComponente', () => {
  let componente: MiComponente;

  // Se ejecuta antes de cada test, para configurar el componente
  beforeEach(() => {
    componente = new MiComponente();
  });

  // Test específico
  it('debería sumar dos números', () => {
    const resultado = componente.sumar(1, 2);
    expect(resultado).toBe(3);  // Verifica que la suma es correcta
  });

  it('debería devolver 0 cuando no hay parámetros', () => {
    const resultado = componente.sumar(0, 0);
    expect(resultado).toBe(0);  // Verifica que la suma de ceros es correcta
  });
});


Anatomía detallada:
describe(): Agrupa todos los tests relacionados con MiComponente.
beforeEach(): Inicializa una nueva instancia de MiComponente antes de cada prueba.
it(): Define un test específico.
expect(): Realiza una afirmación para verificar que el método sumar() devuelve el valor esperado.


Otros elementos útiles en los tests:
Matchers adicionales: Además de .toBe(), puedes usar otros matchers, como .toEqual() (para comparar objetos), .toBeTruthy() (para verificar si algo es verdadero), .toContain() (para verificar elementos en arreglos), etc.

Espías (Spies): En Jasmine, los espías (spyOn()) permiten verificar si ciertos métodos fueron llamados durante una prueba.

it('debería llamar a un método', () => {
  const spy = spyOn(componente, 'metodoEjemplo');
  componente.ejecutarAlgo();
  expect(spy).toHaveBeenCalled();
});
