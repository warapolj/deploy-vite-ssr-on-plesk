## Vite (SSR)

For more information on Vite SSR, please refer to the [ViteJs documentation](https://vitejs.dev/guide/ssr.html).

## Steps to Deploy on Plesk

1. Create a CommonJS File:
   - In the project root, create a file named `index.cjs` to use as the `Application Startup File` on Plesk.
   ```javascript
   async function startApp() {
     await import('./server.js');
   }

   startApp();

2. Move `index.html` out of the project root to the `/public` directory.
3. Update Build Configuration:
    - Modify the build configuration in `vite.config.js` as follows:
    ```javascript
        export default defineConfig({
            // other configurations
            build: {
                rollupOptions: {
                    input: {
                        index: './public/index.html',
                    },
                },
            },
        });
    ```
4. Update Paths in server.js:
    - Ensure that all paths referencing `index.html` in `server.js` are updated accordingly.


## Testing
- Build the production version by running `npm run build`
- After building, the `/dist/client` directory should contain `/public/index.html`.

## Plesk Admin Panel
1. Set the Application Startup File to `index.cjs`.
2. Run the Node.js command `npm run build`.
3. Restart the application.