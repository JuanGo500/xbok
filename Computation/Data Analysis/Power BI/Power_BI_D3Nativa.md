# Enviroment configuration

1. Install node.js.

2. Pbiviz configuration
- Installation pbiviz: `npm i -g powerbi-visuals-tools`
- Installation certificate Windows: `pbiviz --install-cert`

3. Set-up Power BI Desktop `Options>Report settings>Developer mode`

4. Set up Power BI service for developing a visual `Settings>Settings>General>Developer>Enable`

# Visual creation
1. Create visual `pbiviz new visualName`
2. Install additional libraries (required for developing a visual)
`npm install`
or individually
```
npm i d3@^5.0.0 --save
npm i @types/d3@^5.0.0 --save
npm i core-js@3.2.1 --save
npm i powerbi-visuals-api --save-dev
```

# Troubleshooting
## npm is not found in the path
- Restart
- If not found, modify variables

## Not visible in the service
A pesar de haber arrancado, no se visualizaba en el servicio. La solución fue entrar en https://localhost:8080/assets/status 
y volver a refrescar el visual. Se autoriza en el navegador la dirección.
In Edge: `about:flags> search "local host" > enable "localhost without certificate"`

# References
## Official documentation
https://learn.microsoft.com/en-us/power-bi/developer/visuals/environment-setup?tabs=windows

## Tutorials
https://docs.microsoft.com/en-us/power-bi/developer/visuals/develop-circle-card#:~:text=Sign%20in%20to%20PowerBI.com,pane%2C%20select%20the%20Developer%20Visual.

https://docs.microsoft.com/en-us/power-bi/developer/visuals/visual-project-structure

https://docs.microsoft.com/en-us/power-bi/developer/visuals/dataview-mappings



