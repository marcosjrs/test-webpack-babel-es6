## Iniciando proyecto
```
npm init -y
```

## Basado en lo mostrado en la url https://webpack.js.org/guides/installation/

```
npm install --save-dev webpack
npm install --save-dev webpack-cli
```

## Basado en lo mostrado en la url https://webpack.js.org/guides/getting-started/
Apartado donde dice como crear el archivo webpack.config.js y su contenido.
Se modificó el entry path.resolve.... quedando: 

```
const path = require('path');

module.exports = {
    entry: './src/index.js',
    output: {
        filename: 'bundle.js',
        path: path.join(__dirname, '/'),
    },
};
```


## Basado en lo mostrado en la url https://babeljs.io/setup#installation , seleccionando webpack y siguiendo los siguientes pasos que indica

```
npm install --save-dev babel-loader @babel/core
```

Modificamos el webpack.config.js, conel module que indica en el paso "3 Usage" quedando el su contenido como sigue:

```
const path = require('path');

module.exports = {
    entry: './src/index.js',
    output: {
        filename: 'bundle.js',
        path: path.join(__dirname, '/'),
    },
    module: {
        rules: [
            {
                test: /\.m?js$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader",
                    options: {
                        presets: ['@babel/preset-env']
                    }
                }
            }
        ]
    }
};
```

```
npm install @babel/preset-env --save-dev
```

```
// Creamos archivo babel.config.json con el contenido
{
  "presets": ["@babel/preset-env"]
}
```

## Comenzamos con la creación del index que va a cargar el bundle.js y carpeta src con el contenido de los modulos que se cargan finalmente todo en el index.js