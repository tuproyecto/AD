### Component model correspondence rules <a name="component-model-correspondence-rules"></a>

Los Jar generados posterior de la aplicación serán desplegados en servidores provistos por el Servicio de AWS contratado para tal fin.

Debe existir 3 ambientes Desarrollo, Pruebas y Producción, desarrollo corresponde al ambiente local de los programadores, mientras que pruebas será desplegado de manera independiente a producción pero estará desplegado empleando el servicio de AWS, producción será independiente y si y sólo si sera puesto en producción aquellos desarrollos o nuevas características que han sido probadas por desarrolladores, testers y usuarios finales.

Las bases de datos estarán en servidores provistas por AWS, manejando tres ambientes como es el caso del código, desarrollo, pruebas y producción.

Se debe desplegar un repositorio de código, para este caso se emplea Gogs y el versionamiento se hará empleando git, debe existir un solo repositorio alojado en un servidor provisto por el AWS.

Para los desarrolladores los requerimientos de pull serán de acuerdo a la necesidad, para el caso de Push al repositorio principal, solo se harán posterior a la validación del Arquitecto o quien este designe, así los desarrolladores menos experimentados podrán recibir retroalimentación por parte de otros integrantes del equipo.