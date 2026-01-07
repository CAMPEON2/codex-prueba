# codex-prueba
(cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF'
diff --git a/docs/sistema_autonomo_gpt.md b/docs/sistema_autonomo_gpt.md
new file mode 100644
index 0000000000000000000000000000000000000000..e26209cc372c2f632e688f5ba922e61c7c4125ec
--- /dev/null
+++ b/docs/sistema_autonomo_gpt.md
@@ -0,0 +1,74 @@
+# Sistema autónomo para que el GPT funcione solo y mejore día a día
+
+## Objetivo
+Construir un flujo **automático y continuo** que:
+- recopile información diaria sobre inversiones e inmobiliario,
+- genere resúmenes accionables,
+- registre resultados y métricas,
+- aprenda de su propio desempeño para mejorar la calidad con el tiempo.
+
+## 1) Arquitectura del sistema (ciclo diario)
+1. **Ingesta**
+   - Fuentes RSS y webs oficiales (BCE, Fed, INE, Eurostat, NAR, etc.).
+   - Consultoras inmobiliarias (CBRE, JLL, Savills, Knight Frank, Colliers).
+   - Medios financieros (FT, Bloomberg, WSJ, The Economist).
+
+2. **Normalización**
+   - Limpieza de texto y eliminación de duplicados.
+   - Etiquetado por región y tipo de activo (residencial, logístico, oficinas, etc.).
+
+3. **Análisis**
+   - Extracción de señales clave: cambios de tipos, yields, vacancy, precios.
+   - Detección de tendencias y anomalías.
+
+4. **Generación**
+   - Resumen diario/semana y alertas automáticas.
+   - Recomendaciones accionables según región.
+
+5. **Registro de resultados**
+   - Guardar resultados diarios en un log.
+   - Registrar fuentes usadas y métricas de calidad.
+
+6. **Mejora continua (feedback loop)**
+   - Evaluar la utilidad de los resúmenes (feedback humano o métricas).
+   - Ajustar prompts y ponderaciones de fuentes semanalmente.
+   - Comparar resultados frente a benchmarks previos.
+
+## 2) Automatización práctica (sin intervención humana)
+- **Programación diaria** con cron o GitHub Actions.
+- **Pipeline recomendado**:
+  - 06:00: Ingesta + limpieza.
+  - 06:30: Análisis y generación de resumen.
+  - 07:00: Publicación y almacenamiento.
+  - 20:00: Revisión de métricas y retroalimentación.
+
+## 3) Métricas de mejora diaria
+- **Calidad de fuentes**: % de fuentes oficiales vs. medios generalistas.
+- **Cobertura**: nº de regiones/sectores cubiertos por día.
+- **Utilidad**: feedback humano (1–5) o clics en alertas.
+- **Consistencia**: evolución del número de insights útiles por semana.
+
+## 4) Acciones de aprendizaje automático del GPT
+- Guardar diariamente un dataset de:
+  - inputs (noticias, datos),
+  - outputs (resúmenes),
+  - feedback (positivo/negativo).
+- Cada semana:
+  - re-entrenar prompts o ajustar pesos en el ranking de fuentes.
+  - eliminar fuentes irrelevantes o ruidosas.
+
+## 5) Ejemplo de flujo diario (ejecutable)
+1. Descargar feeds.
+2. Procesar y clasificar.
+3. Generar resumen.
+4. Guardar en `outputs/diario/`.
+5. Registrar métricas en `outputs/metricas/`.
+
+## 6) Checklist diario automático
+- [ ] Ingesta completada sin errores.
+- [ ] Resumen diario generado.
+- [ ] Métricas registradas.
+- [ ] Feedback incorporado.
+
+---
+**Resultado esperado:** un GPT que funcione solo, entregue valor diario y se ajuste continuamente para mejorar calidad y relevancia.
EOF
)
