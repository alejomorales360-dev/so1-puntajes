# SO1 · Puntajes

App web (Google Apps Script) para consultar el puntaje de un socio: ranking, historial de asistencias, cuotas y ausencias en actividades obligatorias.

Este repositorio es una de las tres apps que originalmente vivían en un mismo proyecto de Apps Script (Puntajes, Admin, Tesorería). Cada una quedó separada en su propio repositorio, pero **comparten el mismo backend (`Codigo.gs`)** porque todas leen/escriben la misma planilla de Google Sheets.

## Estructura

- `index.html` — interfaz de la app (frontend que corre dentro de Apps Script).
- `Codigo.gs` — backend compartido (`doGet`/`doPost` + toda la lógica de negocio contra Google Sheets).
- `appsscript.json` — manifest del proyecto Apps Script.
- `.clasp.json.example` — plantilla de configuración para [`clasp`](https://github.com/google/clasp). Copia a `.clasp.json` y reemplaza `scriptId` por el ID real del proyecto Apps Script antes de hacer `clasp push`.

## Desarrollo con clasp

```bash
npm install -g @google/clasp
clasp login
cp .clasp.json.example .clasp.json   # y edita el scriptId
clasp push
```

## Notas

- `SS_ID` en `Codigo.gs` apunta a la planilla de Google Sheets compartida entre las 3 apps — no cambiarlo sin coordinar con los otros repos.
- Si vas a desplegar este proyecto como Web App independiente, el `doGet` sin `?page=` sirve `index.html` (esta app).
