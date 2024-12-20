#Imagem base para build do React
FROM node:18 as build  

#Diretório de trabalho dentro do container para /app
WORKDIR /app  

#Copia e instala dependências
COPY package*.json ./  

#Habilita o Corepack e instala todas as dependências listadas no package.json.
RUN corepack enable && npm install  

#Variável de ambiente para o backend
ENV REACT_APP_BACKEND_URL=http://localhost:5000  

#Copia o restante do código para executar o build
COPY . ./  
#Executa o script `build` do React
RUN npm run build  

#Imagem base para servir o React
FROM nginx:latest  

#Remove a configuração padrão do NGINX
RUN rm -rf /usr/share/nginx/html/*  

#Copia os arquivos do React para a pasta do NGINX
COPY --from=build /app/build /usr/share/nginx/html  

#Expõe a porta 80
EXPOSE 80  

#Inicia o NGINX
CMD ["nginx", "-g", "daemon off;"]
