https://docs.microsoft.com/es-es/power-bi/developer/visuals/environment-setup?tabs=windows

Install nodes.js.





 

- Installation pbiviz
'''
npm i -g powerbi-visuals-tools
'''

- Installation certificate
Windows
'''
pbiviz --install-cert

'''

Set up Power BI service for developing a visual.

Install additional libraries (required for developing a visual)
npm i d3@^5.0.0 --save
npm i @types/d3@^5.0.0 --save
npm i core-js@3.2.1 --save
npm i powerbi-visuals-api --save-dev

# Troubleshooting
A pesar de haber arrancado, no se visualizaba en el servicio. La solución fue entrar en https://localhost:8080/assets/status 
y volver a refrescar el visual. Se autoriza en el navegador la dirección.


Tutorial
https://docs.microsoft.com/en-us/power-bi/developer/visuals/develop-circle-card#:~:text=Sign%20in%20to%20PowerBI.com,pane%2C%20select%20the%20Developer%20Visual.


