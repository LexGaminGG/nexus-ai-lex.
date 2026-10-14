# ULTRA AI PRO — proyecto funcional de base

Aplicación web local con chat persistente en SQLite, asistente especializado en programación (incluido Roblox/Luau), generación de imágenes, edición de imágenes y análisis de documentos.

## Requisitos
- Python 3.10 o superior
- Una clave API válida de OpenAI, con acceso a los modelos configurados y facturación según uso
- Conexión a Internet

## Instalación
1. Descomprime el ZIP.
2. Abre una terminal en la carpeta `ultra_ai_pro`.
3. Crea un entorno virtual: `python -m venv .venv`
4. Actívalo: Windows `.venv\\Scripts\\activate`; Linux/macOS `source .venv/bin/activate`.
5. Instala dependencias: `pip install -r requirements.txt`
6. Copia `.env.example` como `.env`.
7. Edita `.env`: introduce `OPENAI_API_KEY` y cambia `APP_PASSWORD` por una contraseña fuerte. No publiques este archivo.
8. Inicia: `uvicorn app:app --host 127.0.0.1 --port 8000`
9. Abre `http://127.0.0.1:8000` e introduce tu `APP_PASSWORD`.

## Funciones reales
- Chat con historial de los últimos 20 mensajes de cada conversación (guardados en SQLite).
- Modo programación, ingeniería, documentos y general.
- Generación PNG mediante el modelo configurado.
- Edición de imágenes PNG/JPG/WEBP con modelo compatible.
- Lectura y análisis de PDF con texto, Word, Excel y archivos de código.
- Descarga autenticada de imágenes generadas.

## Límites
- No incluye ejecución de código generado, despliegue público, vídeo, búsqueda web, creación automática de archivos Word/PDF ni cuentas multiusuario. Estas requieren módulos adicionales.
- Las imágenes y los chats se guardan localmente sin cifrado; evita información sensible.
- Los PDF escaneados requieren OCR no incluido.
- El acceso de imágenes a través de API depende de permisos y modelos disponibles en tu cuenta.
- La edición generativa puede alterar partes no solicitadas.
- No está preparado para exposición directa a Internet: faltan TLS, autenticación multiusuario, límites de frecuencia y medidas adicionales.
- El historial en SQLite se almacena hasta que lo borres; la interfaz no recupera conversaciones previas automáticamente.
- Las claves y los costos de API son responsabilidad del propietario.

## Seguridad
- No subas `.env` a GitHub.
- Usa solo en `127.0.0.1` salvo que añadas seguridad de producción.
- Nunca ejecutes código generado sin un entorno aislado.
- Los archivos adjuntos se procesan en memoria con límite de tamaño.

## Conversación por voz (v1.1)
- Abre **Chat y código**, pulsa **Hablar**, concede acceso al micrófono y pulsa **Detener**.
- La grabación se transcribe en el servidor y se envía al chat automáticamente.
- La respuesta se reproduce con voz sintética femenina seleccionable (Shimmer, Coral, Nova o Sage).
- Activa/desactiva **Responder con voz**; usa **Silenciar** para detener la reproducción.
- Requiere modelos STT y TTS disponibles en tu cuenta y conexión a Internet.
- En `localhost` funciona el micrófono; para usarlo desde otros dispositivos normalmente se requiere HTTPS.
- Es conversación por turnos, no voz en tiempo real con interrupciones.
- La naturalidad depende del modelo TTS; no es posible garantizar que sea indistinguible de una persona.
- El audio se envía al proveedor para transcribirlo y sintetizar la respuesta; revisa su política de privacidad.
- El texto se limita a 4000 caracteres por reproducción. El audio generado no se guarda en disco.
- Se aplican cargos de API por transcripción, chat y síntesis.

## Versión 1.2: especialización de programación
- **Programador experto** seleccionado por defecto.
- Modos adicionales **Roblox/Luau**, **Depuración** y **Arquitectura**.
- Instrucciones reforzadas para entregar código, estructura de archivos, instalación, seguridad y pruebas.
- Se mantienen chat, voz, generación y edición de imágenes, análisis de documentos.
- La especialización se logra mediante instrucciones de sistema: la capacidad real depende del modelo `CHAT_MODEL` y su acceso API. No elimina límites del proveedor ni garantiza ausencia de errores.
- El proyecto no ejecuta ni prueba automáticamente código generado; evita ejecutarlo fuera de un entorno aislado.
