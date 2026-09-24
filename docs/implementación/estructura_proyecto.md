---
sidebar_position: 1
title: Estructura del proyecto
---

# Estructura del proyecto

## Tecnologías

| Capa | Tecnología | Motivo |
|---|---|---|
| Interfaz | React 18 + TypeScript | Componentes reutilizables y tipado del modelo histórico |
| Empaquetado | Vite | Arranque rápido y compilación estática |
| Mapa | Leaflet | Mapa ligero y sin coste de licencia |
| Datos | Archivos JSON | Contenido histórico separado del código y fácil de revisar |
| Pruebas | Vitest | Integración natural con Vite |
| Documentación | Docusaurus | Publicación en GitHub Pages |

## Árbol de directorios

```text
ecclesia-primitiva/
├── public/
│   └── favicon.svg
├── src/
│   ├── components/
│   │   ├── LineaTemporal.tsx
│   │   ├── MapaMediterraneo.tsx
│   │   ├── FichaPersona.tsx
│   │   ├── FichaEvento.tsx
│   │   ├── ListaFuentes.tsx
│   │   └── Cuestionario.tsx
│   ├── data/
│   │   ├── personas.json
│   │   ├── lugares.json
│   │   ├── eventos.json
│   │   ├── viajes.json
│   │   ├── fuentes.json
│   │   └── glosario.json
│   ├── models/
│   │   └── index.ts
│   ├── services/
│   │   ├── filtrarEventos.ts
│   │   ├── validarDatos.ts
│   │   └── buscador.ts
│   ├── pages/
│   │   ├── Inicio.tsx
│   │   ├── Mapa.tsx
│   │   └── Glosario.tsx
│   ├── App.tsx
│   └── main.tsx
├── tests/
│   └── filtrarEventos.test.ts
├── package.json
├── tsconfig.json
└── vite.config.ts
```

## Responsabilidad de cada carpeta

| Carpeta | Contenido |
|---|---|
| `components/` | Piezas visuales reutilizables, sin lógica de negocio |
| `data/` | Contenido histórico en JSON; es lo que revisa el editor |
| `models/` | Interfaces TypeScript que reflejan el diagrama de clases |
| `services/` | Lógica pura (filtrado, búsqueda, validación), fácil de probar |
| `pages/` | Pantallas completas que combinan componentes |
| `tests/` | Pruebas unitarias de los servicios |

## Modelos en TypeScript

```ts
export type TipoEvento =
  | "FUNDACIONAL" | "MARTIRIO" | "CONCILIO"
  | "PERSECUCION" | "VIAJE_MISIONERO" | "ESCRITO" | "POLITICO";

export type NivelCerteza = "EXACTA" | "APROXIMADA" | "TRADICIONAL";

export interface Evento {
  id: string;
  nombre: string;
  descripcion: string;
  anioInicio: number;
  anioFin: number;
  tipo: TipoEvento;
  certeza: NivelCerteza;
  lugarId: string;
  personasIds: string[];
  fuentesIds: string[];
}
```

## Ejemplo de dato (`eventos.json`)

```json
{
  "id": "concilio-jerusalen",
  "nombre": "Concilio de Jerusalén",
  "descripcion": "Reunión de apóstoles y ancianos para decidir si los creyentes no judíos debían cumplir la Ley de Moisés.",
  "anioInicio": 48,
  "anioFin": 50,
  "tipo": "CONCILIO",
  "certeza": "APROXIMADA",
  "lugarId": "jerusalen",
  "personasIds": ["pedro", "santiago-el-justo", "pablo", "bernabe"],
  "fuentesIds": ["hechos-15", "galatas-2"]
}
```

## Convenciones

- Nombres de archivos de componentes en `PascalCase`; servicios y datos en `camelCase` o `minusculas`.
- Cada evento y cada persona debe tener al menos un identificador de fuente (`validarDatos.ts` lo comprueba al arrancar).
- Los servicios no dependen de React, así pueden probarse de forma aislada.

## Puesta en marcha

```bash
npm install
npm run dev      # servidor de desarrollo
npm run test     # pruebas unitarias
npm run build    # versión de producción en dist/
```
