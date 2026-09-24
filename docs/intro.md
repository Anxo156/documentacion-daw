---
sidebar_position: 1
title: Introducción
slug: /intro
---

# Ecclesia Primitiva: atlas interactivo de la Iglesia Primitiva

**Ecclesia Primitiva** es un proyecto de software *ficticio* (creado con fines académicos) que ofrece una aplicación web para explorar la historia de la Iglesia de los primeros siglos: quiénes fueron sus protagonistas, dónde se extendió, qué escribieron y qué acontecimientos marcaron su desarrollo.

## Objetivo

Permitir que estudiantes, docentes y curiosos recorran de forma visual e interactiva el nacimiento y expansión del cristianismo, desde **Pentecostés (c. 30 d. C.)** hasta el **Concilio de Nicea (325 d. C.)**, distinguiendo siempre entre lo que dicen las fuentes y lo que transmite la tradición.

## Contexto histórico en breve

La Iglesia nace en Jerusalén, dentro del judaísmo del Segundo Templo, con los discípulos de Jesús de Nazaret. Tras la persecución que sigue al martirio de Esteban, la fe se extiende a Judea, Samaría y Antioquía de Siria, donde los discípulos son llamados «cristianos» por primera vez (Hechos 11,26). Desde allí, misioneros como Bernabé y Pablo de Tarso la llevan a Asia Menor, Grecia y Roma. En sus primeras décadas la comunidad debe resolver una cuestión decisiva: si los creyentes no judíos debían circuncidarse y cumplir la Ley de Moisés, tema que se trata en el **Concilio de Jerusalén (c. 48-50)**.

En los siglos II y III la Iglesia se organiza en torno a obispos, presbíteros y diáconos, fija el canon de sus escritos, se defiende de acusaciones y de corrientes como el gnosticismo (Ireneo de Lyon, Tertuliano, Justino), y sufre persecuciones locales y, desde Decio (250), generales. Con el Edicto de Milán (313) termina la etapa de persecución.

## Periodización adoptada

| Periodo | Fechas aproximadas | Rasgos principales |
|---|---|---|
| Época apostólica | c. 30 - c. 100 | Jerusalén, misiones paulinas, cartas del Nuevo Testamento, muerte de los apóstoles |
| Padres apostólicos | c. 100 - c. 150 | Didaché, 1 Clemente, Ignacio de Antioquía, Policarpo, Papías |
| Apologistas y consolidación | c. 150 - c. 250 | Justino, Ireneo, Tertuliano, Clemente de Alejandría, Orígenes |
| Persecuciones y tolerancia | c. 250 - 325 | Decio, Diocleciano, Edicto de Milán (313), Concilio de Nicea (325) |

## Hitos que modela la aplicación

| Fecha | Hito | Fuente principal |
|---|---|---|
| c. 30 | Pentecostés en Jerusalén | Hechos 2 |
| c. 34-36 | Martirio de Esteban y dispersión de la comunidad | Hechos 7-8 |
| c. 33-36 | Conversión de Pablo de Tarso | Hechos 9; Gálatas 1 |
| c. 40s | Comunidad de Antioquía; primer uso de «cristianos» | Hechos 11,19-26 |
| c. 48-50 | Concilio de Jerusalén | Hechos 15; Gálatas 2 |
| c. 49 | Expulsión de judíos de Roma bajo Claudio | Suetonio, *Claudio* 25; Hechos 18,2 |
| c. 50-51 | 1 Tesalonicenses, probablemente el escrito cristiano más antiguo | Carta de Pablo |
| c. 62 | Muerte de Santiago, «hermano del Señor» | Flavio Josefo, *Antigüedades* 20 |
| 64 | Incendio de Roma y persecución de Nerón | Tácito, *Anales* 15,44 |
| c. 64-67 | Martirio de Pedro y Pablo en Roma | Tradición (1 Clemente 5) |
| 70 | Destrucción del Templo de Jerusalén | Flavio Josefo, *Guerra de los judíos* |
| c. 96 | Carta de Clemente de Roma a los corintios | 1 Clemente |
| c. 110-112 | Cartas de Ignacio de Antioquía; carta de Plinio a Trajano | Ignacio; Plinio, *Cartas* 10,96 |
| mediados s. II | Martirio de Policarpo de Esmirna (fecha discutida) | Martirio de Policarpo |
| 250 / 303 | Persecuciones de Decio y de Diocleciano | Eusebio; Lactancio |
| 313 / 325 | Edicto de Milán / Concilio de Nicea | Eusebio de Cesarea |

:::note Nota sobre las fechas
Muchas fechas de la Iglesia Primitiva son aproximadas y debatidas por los historiadores. Por eso el sistema guarda, junto a cada fecha, un **nivel de certeza** (exacta, aproximada o tradicional).
:::

## Fuentes que utiliza el proyecto

- **Fuentes cristianas**: Nuevo Testamento (especialmente Hechos de los Apóstoles y cartas paulinas), Didaché, 1 Clemente, cartas de Ignacio, Justino Mártir, Ireneo de Lyon, Tertuliano y la *Historia eclesiástica* de Eusebio de Cesarea (s. IV).
- **Fuentes no cristianas**: Flavio Josefo, Tácito, Suetonio y Plinio el Joven.

## Organización de esta documentación

```text
docs/
├── intro.md                          ← estás aquí
├── análisis/requisitos.md            ← qué debe hacer el sistema
├── diseño/diagrama_clases.md         ← cómo se modela el dominio
├── implementación/estructura_proyecto.md  ← cómo se organiza el código
├── pruebas/analisis_caja_blanca.md   ← cómo se comprueba su corrección
└── despliegue/github_pages.md        ← cómo se publica
```
