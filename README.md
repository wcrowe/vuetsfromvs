# vuetsfromvs


to fix ssl socketio error 

#in vue.config.js
module.exports = {
    devServer: {
        host: "localhost",
        https: {
            key: fs.readFileSync(keyFilePath),
            cert: fs.readFileSync(certFilePath),
        },
        proxy: {
            '^/weatherforecast': {
                target: 'https://localhost:7187/'
            }
        },
        port: 5002
    }
}

#in package.json
  "scripts": {
    "serve": "node aspnetcore-https.js --name=api && vue-cli-service serve --ssl true",
    "dev": "node aspnetcore-https.js && vue-cli-service serve",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
  },
