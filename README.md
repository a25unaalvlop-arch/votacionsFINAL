
Instruccions per instalar dependencies

cd votacions
npm install

cd ../Server
npm install

///////////////////

Instruccions per executar

Per executar el programa en local:
cd Server && node server.js

Una vegada el servidor a arrencat,
cd ..
cd votacions && npm run dev
Pots accedir a la pàgina a traves de localhost i el port obert per vue

Per executar amb docker:

Desde l'arrel del projecte,
docker compose up

///////////////////
