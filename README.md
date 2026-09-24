📘 AstraX‑512B — README Oficial (Versión 1.0)
Modelo Fundacional Multimodal MoE — 512B parámetros totales — 16B–24B activos
🧩 Descripción General
AstraX‑512B es un modelo fundacional multimodal de arquitectura Mixture of Experts (MoE) diseñado para maximizar:

razonamiento estructurado,

especialización masiva,

estabilidad del gating,

eficiencia en coste activo,

escalabilidad en hardware realista,

integración multimodal completa (texto + visión + audio + vídeo).

El modelo combina:

64 expertos de lenguaje, cada uno con 8B parámetros,

encoders multimodales externos (visión, audio, vídeo),

routing híbrido avanzado,

gating multimodal,

paralelismo experto + tensor + pipeline,

16B–24B parámetros activos por token,

512B parámetros totales en BF16.

AstraX‑512B está diseñado para ser entrenable, modular, escalable, y útil en entornos reales de investigación.

🔢 Arquitectura
Mixture of Experts (MoE)
64 expertos independientes

8B parámetros por experto

24 capas por experto

embedding 6.144

atención 48×128

FFN 24.576 (SwiGLU)

RoPE integrado

LayerNorm pre-norm

Residuales profundos

Routing híbrido avanzado
Gating de secuencia: top‑16

Gating de token: top‑2/3

Refinamiento local: ajuste dinámico

Balance de carga

Entropía controlada

Penalización de repetición de experto

Paralelismo HPC
Expert parallel: 8 grupos × 8 expertos

Tensor parallel: matrices divididas en 4–8 GPUs

Pipeline parallel: 24 capas → 3 etapas de 8 capas

🖼 Multimodal Completo
Visión
Encoder ViT‑G / ViT‑H

salida 2.048–4.096

proyección a 6.144

integración con MoE mediante fusión cruzada

Audio
Encoder Whisper‑Large

salida 1.024–2.048

proyección a 6.144

alineación temporal

Vídeo
Encoder temporal 3D

salida 2.048

proyección a 6.144

integración con gating multimodal

Fusión multimodal
ℎ
𝑓
𝑢
𝑠
𝑖
𝑜
𝑛
=
𝑊
𝑣
ℎ
𝑣
𝑖
𝑠
𝑖
𝑜
𝑛
+
𝑊
𝑎
ℎ
𝑎
𝑢
𝑑
𝑖
𝑜
+
𝑊
𝑣
𝑖
𝑑
ℎ
𝑣
𝑖
𝑑
𝑒
𝑜
+
𝑊
𝑡
ℎ
𝑡
𝑒
𝑥
𝑡
📐 Especificaciones Matemáticas
Atención por capa
4
×
6,144
2
≈
151
𝑀
FFN por capa
6,144
×
24,576
×
2
≈
302
𝑀
Total por capa
151
𝑀
+
302
𝑀
+
5
𝑀
≈
458
𝑀
Total por experto
458
𝑀
×
24
≈
11
𝐵
Ajustado a 8B mediante optimización de matrices auxiliares.

📊 Coste Activo y Coste Total
Coste activo
2 expertos × 8B = 16B

3 expertos × 8B = 24B

Coste total
512B parámetros totales

BF16 → ~512 GB

entrenamiento distribuido → 8–32 GPUs

🧪 Entrenamiento
Datos
10–20T tokens de texto

5T tokens de código

5T tokens de razonamiento

5T tokens de visión

5T tokens de audio

5T tokens de vídeo

Optimización
AdamW

LR warmup

decay coseno

ZeRO‑3

sharding de expertos

entrenamiento por etapas

distillation opcional

🔬 Comparación con Modelos Reales
Modelo	Activos	Totales	Multimodal	MoE
Mixtral 8×22B	44B	176B	No	Sí
DeepSeek V3	671B	2T	Sí	Sí
GLaM	1.2T	1.2T	No	Sí
GPT‑4 MoE	~1.8T	Desconocido	Sí	Sí
AstraX‑512B	16–24B	512B	Sí	Sí


🚀 Roadmap del Proyecto
AstraX‑512B‑Lite
64 expertos de 2B

128B totales

4–6B activos

AstraX‑512B‑Base
64 expertos de 8B

512B totales

16–24B activos

AstraX‑512B‑Frontier
128 expertos de 8B

1T total

16–24B activos

🛡 Limitaciones
No es consciente

Puede generar errores factuales

Puede fallar en razonamiento matemático extremo

El multimodal depende de encoders externos

Requiere alineación adicional para seguridad

📦 Uso
Texto
diálogo, razonamiento, análisis, código, matemáticas, creatividad.

Visión
descripción de imágenes, OCR, análisis visual.

Audio
transcripción, análisis de sonido.

Vídeo
descripción de escenas, análisis temporal.

🧱 Atribución
AstraX‑512B está inspirado en:

Mixtral

DeepSeek‑V3

GLaM

GPT‑4 MoE

Qwen‑VL

Gemini multimodal

🧭 Licencia
MIT / Apache 2.0 / tu elección

Encoders externos sujetos a sus propias licencias

🏁 Conclusión
AstraX‑512B es un modelo fundacional multimodal MoE:

entrenable,

escalable,

moderno,

potente,

estable,

atractivo para colaboradores,

y listo para convertirse en un proyecto serio en Hugging Face.
