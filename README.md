# **Get Started**

## **Crear una carpeta vacia y dentro ejecutar:**

    npx create-react-app name-app
    cd name-app
    yarn add -D @craco/craco autoprefixer postcss-nested tailwindcss

### **Crear el archivo *tailwind.config.js en la raiz de tu proyecto*** y dentro del archivo agregar:
    module.exports = {
    purge: ["./src/**/*.html", "./src/**/*.jsx", "./src/**/*.js"],
    theme: {
    extend: {
      screens: {
                xs: { max: "400px" },
            },
          },
        },
      };

### **Crear el archivo *craco.config.js* en la raiz de tu proyecto** y dentro del archivo agregar:

    module.exports = {
    style: {
        postcss: {
        plugins: [
            require("tailwindcss")("./tailwind.config.js"),
            require("postcss-nested"),
          ],
        },
      },
    };

### Luego nos vamos al package.json y usamos **craco** en vez de **react-scripts**

    De esto:

    "scripts": {
      "start": "react-scripts start",
      "build": "react-scripts build",
      "test": "react-scripts test",
      "eject": "react-scripts eject"
    },


    A esto:

    "scripts": {
      "start": "craco start",
      "build": "craco build",
      "test": "craco test"
      "eject": "react-scripts eject"
    },


### **Luego en el archivo *src/index.css*** agregar:

    @tailwind base;
    @tailwind components;
    @tailwind utilities;


### Luego ejecutar nuestro proyecto:
    
    npm start   /  yarn start


### Por si ocurre un error parecido a este

    ./src/index.css (./node_modules/css-loader/dist/cjs.js??ref--5-oneOf-4-1!./node_modules/react-scripts/node_modules/postcss-loader/src??postcss!./src/index.css)
    Error: PostCSS plugin tailwindcss requires PostCSS 8.

### Ejecutar:

    yarn add -D postcss

    o cambiar a la version ^7 del postcss en el archivo package.json:

    "devDependencies": {
     "postcss": "^7.0.0",
    }

### Creditos:
  https://dev.to/ryandunn/how-to-use-tailwind-with-create-react-app-and-postcss-with-no-hassle-2i09
