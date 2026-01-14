# Navigation Drawer com Múltiplas Activities

Este repositório contém um exemplo de **Navigation Drawer** implementado com **múltiplas Activities**, sem uso de Fragments. A abordagem central é uma `BaseActivity` que concentra toda a lógica e o layout do Drawer, permitindo que cada Activity filha injete seu conteúdo em um `FrameLayout` compartilhado.

## Visão geral

O projeto demonstra como:

- criar um **DrawerLayout** reutilizável em uma `BaseActivity`;
- listar itens do menu usando um `ListView`;
- alternar entre Activities conforme o item selecionado;
- manter o estado do item selecionado ao abrir a Activity correspondente.

## Estrutura do projeto

Principais pontos de interesse:

- `NavigationDrawerActivity/AndroidManifest.xml` — declara a `BaseActivity` como launcher e lista as Activities do menu.
- `NavigationDrawerActivity/src/com/navigation/drawer/activity/BaseActivity.java` — centraliza a configuração do Drawer (layout, lista, toggle e navegação).
- `NavigationDrawerActivity/src/com/navigation/drawer/activity/Item*Activity.java` — Activities de exemplo que herdam de `BaseActivity`.
- `NavigationDrawerActivity/res/layout/navigation_drawer_base_layout.xml` — layout do Drawer com `DrawerLayout`, `FrameLayout` e `ListView`.
- `NavigationDrawerActivity/res/layout/activity_main.xml` — layout utilizado pelas Activities de conteúdo.

## Como a navegação funciona

1. A `BaseActivity` carrega o layout `navigation_drawer_base_layout.xml`.
2. O menu do Drawer é populado com um array (`listArray`) e um `ArrayAdapter`.
3. Ao clicar em um item, a `BaseActivity` chama `openActivity(position)`.
4. O método abre a Activity correspondente (`Item1Activity` até `Item5Activity`).
5. Cada Activity filha injeta sua interface no `FrameLayout` da `BaseActivity` com `getLayoutInflater().inflate(...)`.
6. O item do menu é marcado e o título da ActionBar é atualizado na Activity filha.

## Pré-requisitos

- Android SDK com **API 14** (alvo definido em `project.properties`).
- Ambiente compatível com projetos **Android (Ant/ADT)**, ou importação manual para o Android Studio.

## Como executar

### Opção 1: Android Studio (importação manual)

1. Abra o Android Studio.
2. Selecione **Open** e aponte para a pasta `NavigationDrawerActivity`.
3. Ajuste o **SDK** e o **target** caso necessário.
4. Sincronize e execute no emulador ou dispositivo.

### Opção 2: Ant/ADT (projeto legado)

Se você utiliza o fluxo antigo com Ant/ADT:

1. Importe o projeto no Eclipse/ADT.
2. Garanta que o `target=android-14` está disponível.
3. Execute como **Android Application**.

## Personalização

- **Itens do menu**: edite `listArray` em `BaseActivity.java`.
- **Layouts por tela**: troque o layout inflado em cada `Item*Activity`.
- **Imagens**: as Activities de exemplo usam `R.drawable.image1`, `image2`, etc.

## Observações

- O objetivo é demonstrar a navegação **sem Fragments**.
- A `BaseActivity` é responsável por abrir a primeira tela na primeira execução (`isLaunch`).

## Origem do projeto

Este repositório é um **fork** do projeto original de exemplo publicado por **dipen-patel90**, no GitHub, sob o nome **Navigation-Drawer-With-Multiple-Activity**. Se você quiser consultar a versão original, pesquise pelo repositório do autor no GitHub.

## Licença

Este projeto é apenas um exemplo educacional. Caso queira reutilizar o código, adapte conforme a necessidade do seu app.
