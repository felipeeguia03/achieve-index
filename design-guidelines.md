# Achieve — Design Guidelines

> Documento vivo. Refleja las decisiones de diseño activas en `index.html`.

---

## 1. Identidad visual

### Paleta de colores
| Variable CSS     | Valor       | Uso                                              |
|-----------------|-------------|--------------------------------------------------|
| `--green`        | `#5C6B3A`   | Fondos hero/CTA, texto de marca, dots           |
| `--green-dark`   | `#4a5630`   | Footer, hover states                            |
| `--cream`        | `#F5F0E8`   | Fondo principal, secciones de contenido          |
| `--gold`         | `#C9A84C`   | Acentos, CTAs, el punto en "Achieve.", quotes    |
| `--white`        | `#ffffff`   | Tarjetas, mensajes del chat, backgrounds internos|
| `--text-dark`    | `#2a2a2a`   | Texto de cuerpo principal                        |
| `--text-muted`   | `#6b6b6b`   | Texto secundario, fechas, handles               |

**Lógica de contraste**: verde oliva + crema es la pareja dominante. El dorado aparece exclusivamente como acento — nunca como fondo de área grande. El blanco es neutro interno, nunca fondo de sección.

### Tipografía
- **Serif** (`Georgia, 'Times New Roman', serif`): títulos grandes, subtítulos, numeración de pasos, itálicas de énfasis. Transmite calidez y autoridad sin ser formal en exceso.
- **Sans-serif** (`system-ui, -apple-system, 'Segoe UI', sans-serif`): cuerpo, labels, UI pequeña. Neutro, legible a tamaños chicos.
- **Sin Google Fonts**: la página carga instantáneo y no depende de terceros. Las fuentes del sistema en Mac/iOS/Android son excelentes.

### Espaciado y ritmo
- Secciones principales: `padding: 76px 24px` en desktop.
- Max-width de contenido: `800px` centrado. Nunca texto a full-bleed.
- Responsive breakpoint: `640px` (mobile-first desde ese punto).

---

## 2. Filosofía de conversión

La página tiene una estructura de embudo claro. Cada sección tiene un trabajo específico:

| Sección          | Trabajo                                               |
|-----------------|-------------------------------------------------------|
| **Hero**         | Capturar la atención y dar el gancho emocional ("No estás solo"). El chat mockup demuestra cómo funciona en 3 segundos. |
| **Trust Bar**    | Romper objeciones inmediatas ("¿es una app? ¿necesito algo?"). Tres palabras: humano, diario, sin fricciones. |
| **Cómo funciona**| Reducir la incertidumbre. El cliente necesita saber exactamente qué va a pasar antes de contactar. |
| **Carousel de fotos** | Prueba social visual. No son fotos de stock — son capturas reales enviadas por clientes. Esto es evidencia, no decoración. |
| **Testimonios**  | Objeciones específicas resueltas por pares ("yo tampoco era constante"). Más creíbles que cualquier copy del dueño. |
| **CTA**          | Convertir. El micro-copy "Respondo en menos de 1 hora" elimina el miedo al silencio. |
| **Botón flotante** | Captura de intención tardía. El usuario que llega hasta los testimonios o los términos legales y quiere contactar no debe tener que scrollear hasta arriba. |

### Por qué no hay precios en la página
Intencionalmente ausente. El servicio es personalizado y la charla de 15 minutos es el paso de conversión. Mostrar precio antes de generar valor reduce la conversión — el cliente no tiene contexto para saber si vale la pena.

---

## 3. Principios de copy

**Tono**: cálido, directo, sin formalismos. Tuteo siempre. Sin signos de exclamación excesivos.

**Persona**: el visitante es alguien que quiere cambiar algo concreto en su vida pero le cuesta la constancia. No es un atleta ni un optimizador — es alguien normal que posterga.

**Voz**: Felipe habla en primera persona en los pasos ("Estoy todos los días", "Estoy cuando más cuesta"). Eso es intencional — el servicio es una relación entre personas, no una plataforma.

**Lo que nunca debe aparecer en el copy**:
- Palabras como "transformar", "potencial", "empoderar" — souenan a coaching genérico.
- Garantías de resultados — no solo es deshonesto, viola los términos de servicio.
- Precios en la primera pantalla visible.

---

## 4. Componentes clave

### Chat Mockup (hero)
Es el elemento más importante de la página. Demuestra de forma concreta cómo se siente el servicio. Las conversaciones son reales (tomadas de chats de clientes). Mantener siempre timestamps realistas y mensajes cortos — refleja cómo se comunica realmente Felipe.

### Carousel de fotos
Las fotos son la prueba social más poderosa porque son contextuales: no es un testimonio escrito, es evidencia de que alguien cumplió. Los tags ("Gym · día 5", "Lectura · día 9") generan FOMO positivo — el visitante puede imaginarse a sí mismo en esa foto.

El carousel hace auto-avance cada 4s para que el visitante vea todas las actividades incluso sin interacción.

### Testimonios
Las comillas decorativas (`"`) son intencionales aunque semiinvisibles (opacity 22%) — añaden peso tipográfico sin competir con el texto. No usar estrellas ⭐ — se ven genéricas y de e-commerce.

---

## 5. Mejoras futuras sugeridas

### Prioridad alta
- [ ] **Video corto** (30-60s) de Felipe explicando el servicio — puede ir en el hero o en una sección propia. El video multiplica la confianza porque humaniza el servicio.
- [ ] **FAQ section** — las 5 preguntas más frecuentes antes del CTA. Reduce la fricción de contacto para los indecisos.
- [ ] **og:image real** — cuando el dominio esté activo, generar una imagen 1200×630px con el branding para que los links de WhatsApp/IG muestren preview.

### Prioridad media
- [ ] **Contador social**: "Más de X personas ya arrancaron su primer objetivo" — una vez que haya suficientes clientes para que el número sea creíble (≥20).
- [ ] **Precio o rango de precio**: Una vez establecido el precio fijo, agregarlo en el CTA o en una sección de FAQ para pre-calificar leads.
- [ ] **Sección de áreas** (gym, estudio, lectura, alimentación, etc.) con íconos simples — ayuda al visitante a verse reflejado en un objetivo concreto.

### Prioridad baja
- [ ] Dark mode — no urgente, el target no lo va a pedir.
- [ ] Internacionalización — solo si el servicio escala fuera de Argentina.
- [ ] Analytics — agregar Google Analytics o Plausible cuando se quiera medir conversiones.

---

## 6. Notas técnicas

- **Sin frameworks, sin bundler**: todo está en `index.html`. Se puede editar con cualquier editor de texto y subir a cualquier hosting.
- **Sin dependencias externas en runtime**: cero requests a CDNs, Google Fonts, etc. La página funciona offline.
- **El JS es mínimo y autocontenido**: dos IIFEs al final del body. No bloquean el render.
- **Imágenes**: `loading="lazy"` en las fotos del carousel. El logo y el chat no tienen lazy porque están above the fold.
- **SEO básico**: meta description, Open Graph, JSON-LD LocalBusiness. Para SEO avanzado sería necesario un dominio propio y contenido de blog.
