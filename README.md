# Uniswap Documentation

This web application contains all documentation for Uniswap products. It is built using [Docusaurus 2](https://v2.docusaurus.io/), a modern static website generator.


# Project Layout

### Uniswap documentation is broken down into four sections:
- Concepts - General Uniswap information or concepts useful for using Uniswap products, such as *Liquidity* and *Fees*
- Contracts - Uniswap smart contracts such as the V3 Contracts or *Permit2*
- SDKs - Uniswap integrations such as the *v3-sdk* and the *Swap Widget*
- APIs - The Uniswap APIs such the *Subgraph API*

### Each item in a section should include the following:
- *Overview*
- *Guides*
- *Technical Reference*

## Adding Documentation

### Overview
A product overview should address points such as:

- What are the high level components of the product?
- What what is the high level functionality the product offers?
- Where does the source code of the product live?
- Where does the code artifact live (eg *npm*) and how does someone integrate with it?

A good example is the [V3 Smart Contracts](./docs/contracts/v3/overview.md).

### Guides
Guides should ensure users can easily integrate with the product by including the following parts:
- An introduction that gives the developer the required context and a summary of what the guide will cover and result in/
- A walk-through of the provided example code. The guide should not directly include large blocks of code, but should instead reference/link to this code as needed, including snippets sparingly when required.
- An output or end state that users can test against

A good example is the [V3 SDK Guides](./docs//sdk/v3/guides/01-quick-start.md).

### Technical References
This should contain the technical reference for the exported interfaces. A good example is the [V3 Smart Contracts](./docs/contracts/v3/reference/overview.md).


# Contributing to Uniswap Docs

## Guidelines
Contributing to the docs site is a great way to get involved in the dev community and help other developers along the way! Check out our guidelines [here](./CONTRIBUTING.md).

## Checklist for adding a new product

- Did I pick the right section for the product? 
- Did I create the product folder?
- Did I introduce any new concepts? If so add under */concepts/<category_name><product_name>*
- Did I include an Overview of the product under *<category_name><product_name>/overview* ?
- Did I include Guides of the product under *<category_name><product_name>/guides* ?
- Did I include Technical Reference of the product under *<category_name><product_name>/reference* ?
- Did I open a PR using the the [contributing](./CONTRIBUTING.md) guidelines?

## Checklist example

Let's walk through an example by considering the *Permit2* smart contract:
-  Did I pick the right section for the product? 
    - In this case, [contracts](./docs/contracts/) 
- Did I create the product folder? 
    - In this case, [yes](./docs/contracts/permit2/)
- Did I introduce any new concepts? 
    - No
- Did I include an Overview of the product under */contracts/permit2/overview* ?
    - Yes, I did add them [here](./docs/contracts/permit2/overview.md)
- Did I include Guides of the product under *contracts/permit2/guides* ?
    - No, they should be added [here](./docs/contracts/permit2/guides)
- Did I include Technical Reference of the product under *contracts/permit2/reference* ?
    - Yes I added them [here](./docs/contracts/permit2/reference)
- Did I open a PR using the the [Contributing](./CONTRIBUTING.md) guidelines?
    - Yes

# How to generate markdown files from solidity Natspec comments

Install solidity doc gen
`npm install solidity-docgen`

Get the correct compiler version
`npm install -D solc-0.7@npm:solc@0.7.6`

Put the updated template `contract.hbs` in a /templates folder under the same directory as /contracts that you want to generate

Run `npx solidity-docgen --solc-module solc-0.7 -t ./templates`

# How to gernerate markdown files from typescript commments

`npm install --save-dev typedoc typedoc-plugin-markdown`

`typedoc --out <docs> src/index.ts`

see https://www.npmjs.com/package/typedoc-plugin-markdown for details

# How to Update search indices with algolia

create .env file with `APPLICATION_ID` and the `API_KEY` (write access)
Edit config.json file with

- start url from updated website
- sitemap url from updated website: ex) for docs: https://docs.uniswap.org/sitemap.xml
- "v3-docs" index name
- install jq : `brew install jq`
  run `docker run -it --env-file=.env -e "CONFIG=$(cat ./config.json | jq -r tostring)" algolia/docsearch-scraper`

## Installation

```console
yarn install
```

## Local Development

```console
yarn run start
```

This command starts a local development server and open up a browser window. Most changes are reflected live without having to restart the server.

## Clear cache

```console
yarn docusaurus clear
```

## Build

```console
yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.