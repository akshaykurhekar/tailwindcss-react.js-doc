# Tailwindcss-react.js-doc
steps to add tailwindcss in react.js project.

  ## Creating your project:
      
      npx create-react-app my-project
      cd my-project
  
  ## Install Tailwind via npm
  
      npm install -D tailwindcss@npm:@tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
                                        
                                        OR
      
      yarn add -D tailwindcss@npm:@tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
      
  ## Install and configure CRACO
  
      npm install @craco/craco
                OR 
      yarn add @craco/craco 
      
  Once it’s installed, update your scripts in your package.json file to use craco instead of react-scripts for all scripts except eject:
  
      {
    // ...
    "scripts": {
     "start": "react-scripts start",
     "build": "react-scripts build",
     "test": "react-scripts test",
     "start": "craco start",
     "build": "craco build",
     "test": "craco test",
      "eject": "react-scripts eject"
      },
     }
     
  
  Next, create a craco.config.js at the root of our project and add the tailwindcss and autoprefixer as PostCSS plugins:
  
  
      // craco.config.js
      module.exports = {
        style: {
          postcss: {
          plugins: [
          require('tailwindcss'),
          require('autoprefixer'),
         ],
        },
      },
     }
   
  
## Create your configuration file

  Next, generate your tailwind.config.js file:
  
    npx tailwindcss init
    
  This will create a minimal tailwind.config.js file at the root of your project:
  
     // tailwind.config.js
      module.exports = {
        purge: [],
        darkMode: false, // or 'media' or 'class'
        theme: {
          extend: {},
        },
        variants: {
          extend: {},
        },
        plugins: [],
      }
    
   ## Configure Tailwind to remove unused styles in production  
   
      // tailwind.config.js
      module.exports = {
       purge: [],
       purge: ['./src/**/*.{js,jsx,ts,tsx}', './public/index.html'],
        darkMode: false, // or 'media' or 'class'
        theme: {
          extend: {},
        },
        variants: {
          extend: {},
        },
        plugins: [],
      }
    
    
   ## Include Tailwind in your CSS
   
   Open the ./src/index.css file that Create React App generates for you by default and use the @tailwind directive to include Tailwind’s base, components, and utilities styles, replacing the original file contents:
   
      /* ./src/index.css */
      @tailwind base;
      @tailwind components;
      @tailwind utilities;

Tailwind will swap these directives out at build-time with all of the styles it generates based on your configured design system.

Read our documentation on adding base styles, extracting components, and adding new utilities for best practices on extending Tailwind with your own custom CSS.

Finally, ensure your CSS file is being imported in your ./src/index.js file:

       // src/index.js
        
        import React from 'react';
        import ReactDOM from 'react-dom';
       
        import './index.css';
        import App from './App';
        import reportWebVitals from './reportWebVitals';

        ReactDOM.render(
          <React.StrictMode>
            <App />
          </React.StrictMode>,
          document.getElementById('root')
        );

        // ...
        
        
