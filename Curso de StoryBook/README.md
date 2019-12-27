# Curso de StoryBook for frontend<!-- omit in toc -->

## Tabla de Contenido<!-- omit in toc -->
- [Sobre Storybook](#sobre-storybook)
- [Instalación](#instalaci%c3%b3n)

# Sobre Storybook
Storybook es una librería javascript que permite probar los componentes gráficos por medio de la separación de la lógica de negocio y del contexto de la aplicación.

Storybook soporta actualmente frameworks y librerías tales como: React, Vue, Angular, Mithril, Marko, HTML, Svelte, Meteor, and Ember

https://storybook.js.org/docs/basics/introduction/

# Instalación
En un proyecto de React

```bash
npx create-react-app storybookApp
cd storybookApp
npx -p @storybook/cli sb init --type react
```

Para ejecutar storybook

```bash
npm run storybook
o
yarn storybook
```

