
:prfocus
:prsln
:prmvp

```
Execute : Step 3: Set Up the Development Environment

Be very specific and give all the commands or actions I need to do. I rely any on you. I can't write or do something if you have not explain it to me first.

I'm using webstorm as an IDE.
```
To set up the development environment for your event management platform using Angular, TailwindCSS, and Firebase, follow these specific steps. These instructions assume you are using WebStorm as your IDE and have Node.js installed on your system. If Node.js is not installed, download and install it from [https://nodejs.org/](https://nodejs.org/) before proceeding.

### Step 3: Set Up the Development Environment

#### A. Initialize Angular Project

1. **Install Angular CLI**: Open WebStorm's integrated terminal and run the following command to install Angular CLI globally on your machine. This tool is necessary for creating an Angular project, generating application and library code, and performing a variety of ongoing development tasks.

   ```bash
   npm install -g @angular/cli
   ```

2. **Create New Angular Project**: Use Angular CLI to generate a new project. Replace `my-event-platform` with your project name.

   ```bash
   ng new my-event-platform --style=scss
   ```

   When prompted for Angular routing, you can choose `Yes` or `No` based on your preference. This guide assumes you select `No`.

3. **Navigate to Project Directory**: Change your current directory to the newly created project folder.

   ```bash
   cd my-event-platform
   ```

#### B. Integrate TailwindCSS

1. **Install TailwindCSS**: Within your project directory, install TailwindCSS, its peer dependencies, and Angular builders that support custom webpack configuration by running:

   ```bash
   npm install -D tailwindcss postcss autoprefixer @angular-builders/custom-webpack
   ```

2. **Initialize TailwindCSS**: Generate `tailwind.config.js` and `postcss.config.js` files by running:

   ```bash
   npx tailwindcss init -p
   ```

3. **Configure TailwindCSS in Angular**: Modify the `angular.json` file to use custom webpack configuration for building your project.

    - Find the `projects > my-event-platform > architect > build` section.
    - Replace the `builder` value with `@angular-builders/custom-webpack:browser`.
    - Add a new `options > customWebpackConfig` object:
      ```json
      "customWebpackConfig": {
        "path": "./extra-webpack.config.js"
      }
      ```
    - Repeat the above steps for the `projects > my-event-platform > architect > serve` section, changing its `builder` to `@angular-builders/custom-webpack:dev-server`.

4. **Create Custom Webpack Configuration File**: Create a new file named `extra-webpack.config.js` in your project root and add the following content to enable TailwindCSS processing:

   ```javascript
   module.exports = {
     module: {
       rules: [
         {
           test: /\.scss$/,
           loader: 'postcss-loader',
           options: {
             postcssOptions: {
               ident: 'postcss',
               syntax: 'postcss-scss',
               plugins: ['postcss-import', 'tailwindcss', 'autoprefixer'],
             },
           },
         },
       ],
     },
   };
   ```

5. **Include Tailwind in Your Styles**: Open `src/styles.scss` and add the following lines to import Tailwind directives:

   ```scss
   @import 'tailwindcss/base';
   @import 'tailwindcss/components';
   @import 'tailwindcss/utilities';
   ```

#### C. Firebase Project Setup

1. **Create Firebase Project**:
    - Visit [Firebase Console](https://console.firebase.google.com/).
    - Click on "Add project" and follow the on-screen instructions to create a new Firebase project.

2. **Initialize Firebase in Your Angular Project**:
    - Install Firebase tools and Angular Firebase integration by running:

      ```bash
      npm install firebase @angular/fire
      ```

    - Use the Firebase console to create a new web application associated with your Firebase project and obtain your Firebase configuration object.

3. **Configure Firebase in Your Angular Project**:
    - Create a new file in your `src/environments` folder named `environment.prod.ts` for production environment variables, and ensure your Firebase configuration is added to both this file and the existing `environment.ts` for development. The configuration will look something like this:

      ```typescript
      export const environment = {
        production: false, // true for environment.prod.ts
        firebase: {
          apiKey: "your-api-key",
          authDomain: "your-auth-domain",
          projectId: "your-project-id",
          storageBucket: "your-storage-bucket",
          messagingSenderId: "your-messaging-sender-id",
          appId: "your-app-id"
        }
      };
      ```

With these steps, you have successfully set up your development environment for the Angular project with TailwindCSS and Firebase integration in WebStorm. You're now ready to start developing your event management platform.