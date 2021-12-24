# Perlego EBook Downloader

**Solamente para uso personal.** 

Los estudiantes universitarios que han usado Perlego antes saben que descargar libros electrónicos para verlos sin conexión no es fácil. Este repositorio contiene scripts que ayudan a los usuarios que pagan a descargar sus libros electrónicos sin problemas.

** Para el caso de uso más básico (menos de ~ 200 páginas): **
1. Abra Ebook en un navegador (compatible con PDF y ePub).
2. Vaya a la página que desea comenzar a imprimir.
3. Abra la consola de desarrollador de Chrome [a través de la interfaz de usuario] (https://developers.google.com/web/tools/chrome-devtools/open#chrome).
4. Pegue el contenido de `PerlegoContent.js` en la consola y presione enter.
5. Ingrese `printPages (startPage, endPage)` en la consola, donde `startPage` es el número de página en la que desea comenzar a imprimir y` endPage` es el número de página de la página en la que desea terminar.
6. Espere a que la secuencia de comandos termine de ejecutarse y se le solicitará que guarde el pdf.
7. Si las imágenes no se cargan, intente esperar a que se carguen y luego [imprimir de nuevo manualmente] (https://support.google.com/chrome/answer/1069693).
8. Actualiza la página para volver al eReader de Perlego.



Si desea descargar un libro de texto completo, se recomienda que lo descargue en secciones de alrededor de 150 páginas para reducir la carga en el navegador. A continuación, puede combinar los archivos PDF utilizando herramientas externas como `pdfunite`.

Tenga en cuenta que `PerlegoContent.js` no guarda el menú (esquema) del pdf, por lo que debe utilizar` PerlegoOutline.js` como se describe a continuación.

** (Solo PDF) Procedimiento para descargar un libro de texto completo con el menú intacto: **
1. Descargue todas las secciones del Ebook usando `PerlegoContent.js`, asegúrese de nombrar sus archivos PDF` part_1.pdf`, `part_2.pdf`, etc. en la carpeta` Descargas`.
2. Asegúrese de tener instalado `poppler-utils` para combinar los archivos PDF, y` fntsample` instalado para agregar el esquema.
3. Ejecute `PerlegoOutline.js` desde la página 'Tabla de contenido' del libro electrónico (entre 'Detalles del libro' y 'Relacionados') en la consola del desarrollador.
4. (opcional) Puede personalizar el `outline.txt` descargado de acuerdo con [esta especificación] (http://manpages.ubuntu.com/manpages/bionic/man1/pdfoutline.1.html).
5. En la carpeta `Descargas`, abra una terminal local y ejecute los siguientes comandos:

	```
	# Combine the pdfs into one
	pdfunite part_*.pdf temp.pdf

	# Add the outline of the pdf
	pdfoutline temp.pdf outline.txt output.pdf

	# Clean up
	rm part_*.pdf temp.pdf outline.txt
	```

* Futuro: Agregue soporte para descargar libros ePub como `.epub` en lugar de` .pdf`. *
