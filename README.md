![This is an image](https://www.google.com/imgres?imgurl=https%3A%2F%2Fmma.prnewswire.com%2Fmedia%2F1457892%2FLexisNexis_Logo.jpg%3Fp%3Dfacebook&imgrefurl=https%3A%2F%2Fwww.prnewswire.com%2Fnews-releases%2Flexisnexis-introduces-nexis-data-lab-301249547.html&tbnid=LU0APXcTmRDCcM&vet=12ahUKEwjJjdisjpb1AhXWALcAHRG5Ac8QMygAegUIARDJAQ..i&docid=Ut_y26MYglCATM&w=1966&h=1030&q=lexisnexis&ved=2ahUKEwjJjdisjpb1AhXWALcAHRG5Ac8QMygAegUIARDJAQ)
# How to host Swagger API documentation with GitHub Pages
[<img alt="The blog of Peter Evans: How to Host Swagger Documentation With Github Pages" title="View blog post" src="https://peterevans.dev/img/blog-published-badge.svg">](https://peterevans.dev/posts/how-to-host-swagger-docs-with-github-pages/)

T is a template for using the [Swagger UI](https://github.com/swagger-api/swagger-ui) to dynamically generate beautiful documentation for your API and host it for free with GitHub Pages.

The template will periodically auto-update the Swagger UI dependency and create a pull request. See the [GitHub Actions workflow here](.github/workflows/update-swagger.yml).

The example API specification used by this repository can be seen hosted at [https://peter-evans.github.io/swagger-github-pages](https://peter-evans.github.io/swagger-github-pages/).

## Steps to use this template

1. Click the `Use this template` button above to create a new repository from this template.

2. Go to the settings for your repository at `https://github.com/{github-username}/{repository-name}/settings` and enable GitHub Pages.

    ![Headers](/screenshots/swagger-github-pages.png?raw=true)
    
3. Browse to the Swagger documentation at `https://{github-username}.github.io/{repository-name}/`.


## Steps to manually configure in your own repository

1. Download the latest stable release of the Swagger UI [here](https://github.com/swagger-api/swagger-ui/releases).

2. Extract the contents and copy the "dist" directory to the root of your repository.

3. Move the file "index.html" from the directory "dist" to the root of your repository.
    ```
    mv dist/index.html .
    ```
    
4. Copy the YAML specification file for your API to the root of your repository.

5. Edit [index.html](index.html) and change the `url` property to reference your local YAML file. 
    ```javascript
        const ui = SwaggerUIBundle({
            url: "swagger.yaml",
        ...
    ```
    Then fix any references to files in the "dist" directory.
    ```html
    ...
    <link rel="stylesheet" type="text/css" href="dist/swagger-ui.css" >
    <link rel="icon" type="image/png" href="dist/favicon-32x32.png" sizes="32x32" />
    <link rel="icon" type="image/png" href="dist/favicon-16x16.png" sizes="16x16" />    
    ...
    <script src="dist/swagger-ui-bundle.js"> </script>
    <script src="dist/swagger-ui-standalone-preset.js"> </script>    
    ...
    ```
    
6. Go to the settings for your repository at `https://github.com/{github-username}/{repository-name}/settings` and enable GitHub Pages.

    ![Headers](/screenshots/swagger-github-pages.png?raw=true)
    
7. Browse to the Swagger documentation at `https://{github-username}.github.io/{repository-name}/`.

   The example API specification used by this repository can be seen hosted at [https://peter-evans.github.io/swagger-github-pages](https://peter-evans.github.io/swagger-github-pages/).
