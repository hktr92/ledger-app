# ledger-app

this is a simple web app that helps you manage your personal financial situation.

## features
features are split in two parts: mvp and plus.

- mvp:
  - add various accounts
  - add items to your ledger
    - possibility to add sub-items for an item
  - **clearly** determine whether something has been processed or not
    - possibility to add a time for auto-status update
  - add transfers for your items
    - e.g. having two accounts named "active" and "savings:, you want to add 1000 € to savings account. this will perform two entries:
      - one decrease for "active" account;
      - one increase for "savings" account;
    - option to convert between currencies
  - recursive operations, e.g. you define a salary
  - clean and good overview of what will happen in the next X time-frame
  - pgp-based file encryption
  - multiple currencies and exchange based on country-level provided API
- plus:
  - various statistics (e.g. graph of monthly spending)
  - tutorial and / or demo mode
  - monthly budget: define your income, your expenses and let them be recursive each month.
- beyond:
  - i'm waiting for your proposals for this project.

>**DISCLAIMER**: even if this web app helps you, it doesn't need to be used as a financial advisor. integration with various banking systems is unlikely,
> and it should NOT be used in an enterprise, due to complicated accounting for each and every country.
> additionally, this tool can't predict inter-currency spendings and incomes due to volatility of currency's future, so use it with a grain of salt and some managing here and there. this app will try to save the exchange rate of the past date of your transaction (e.g. if you exchange RON for EUR in 08.02.2022, that value will be stored on save.)

## supported exchange rate systems
yes, there are some various currency exchange services, but i recommend using the one from your country's national bank.
if no such api exists, you can use the "default" option as a fallback. 

anyway, here's a list of apis that ledger-app consumes for currency exchange:
- romania: bnr (romania national bank) -- https://www.bnr.ro/nbrfxrates.xml

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Special Directories

You can create the following extra directories, some of which have special behaviors. Only `pages` is required; you can delete them if you don't want to use their functionality.

### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/assets).

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/components).

### `layouts`

Layouts are a great help when you want to change the look and feel of your Nuxt app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/layouts).


### `pages`

This directory contains your application views and routes. Nuxt will read all the `*.vue` files inside this directory and setup Vue Router automatically.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/get-started/routing).

### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` and add its path to plugins in `nuxt.config.js`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/plugins).

### `static`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/static/robots.txt` is mapped as `/robots.txt`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/static).

### `store`

This directory contains your Vuex store files. Creating a file in this directory automatically activates Vuex.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/store).
