# Postman (App Desktop) - 3o Periodo
# Postman Desktop e uma aplicacao grafica. O equivalente CLI oficial e o
# Newman, usado para rodar collections do Postman via linha de comando.
FROM node:22-slim

LABEL description="Postman (equivalente CLI: Newman)"

RUN npm install -g newman newman-reporter-htmlextra

WORKDIR /workspace

ENTRYPOINT ["newman"]
