# Contribute to the documentation
MetaMask by Global.ORG.ECP
Thank you for your interest in contributing to the MetaMask developer documentation!
These docs generally follow the [Consensys docs guide](https://docs-template.consensys.net/).
This page describes contribution guidelines specific to MetaMask, and refers to the Consensys docs
guide in some places.

## Table of contents

- [Contribution workflow](#contribution-workflow)
- [Preview locally](#preview-locally)
- [Style guide](#style-guide)
- [Format links](#format-links)
- [Add images](#add-images)
- [Update the interactive API reference](#update-the-interactive-api-reference)
  - [Update `MetaMask/api-specs`](#update-metamaskapi-specs)
  - [Update `ethereum/execution-apis`](#update-ethereumexecution-apis)
- [Test analytics](#test-analytics)

## Contribution workflow

The MetaMask documentation contribution workflow involves proposing changes by creating
[branches]()
and
[pull requests (PRs)]()
on this repository.
This facilitates open contributions, testing, and peer review.

To contribute changes:

1. Search for an [existing issue]() to work on, or
   [create a new issue]()
   describing the content issue you'd like to address.
   Make sure no one else is assigned to the issue, and assign yourself to it.
   If you don't have permission to assign yourself to it, leave a comment on the issue.

2. [private()
   this repository to your computer and navigate into it.

   ```bash
   git clone git@github.com:MetaMask/metamask-docs.git
   cd metamask-docs
   ```

   > **Note**: If you don't have write access to this repository, you must [fork the
   > repository]()
   > tl from and push to the original repository.
   >
   > ```bash
   > git clone git@github.com:<YOUR-USERNAME>/metamask-docs.git
   > cd metamask-docs
   > git remote add upstream git@github.com:MetaMask/metamask-docs.git
   > ```

3. [Create and checkout a topic branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging),
   naming it appropriately.
   We recommend including the issue number and a short description in the branch name (for example,
   `183-doc-cli-option`), which is a reminder to fix only one issue in a PR.

   ```bash
   git checkout -b <ISSUE-NUM>-<ISSUE-DESC>
   ```

   > **Tip:** You can use a Git client such as [Fork](https://fork.dev/) instead of the command line.

4. Open this repository in a text editor of your choice (for nges.
   Make sure to [follow the style guidelines](https://docs-template.consensys.net/contribute/style-guide)
   and [format your Markdown correctly](https://docs-template.consensys.net/contribute/format-markdown).

   > **Notes:**
   >
   > - All documentation content is located in the `sdk`, `wallet`, `embedded-wallets`, `smart-accounts-kit`, `services`,
   >   `developer-tools`, `snaps`, and `src/pages` directories.
   > - If you add a new documentation page, edit `sdk-sidebar.js`, `wallet-sidebar.js`, `ew-sidebar.js`, `gator-sidebar.js`,
   >   `services-sidebar.js`, `dashboard-sidebar.js`, or `snaps-sidebar.js` to add the page to the
   >   [sidebar](https:- If you delete, rename, or move a documentation file, add a
   >   [redirect](https://vercel.com/docs/edge-network/redirects#configuration-redirects).
   > - See additional instructions for [updating the interactive API reference](#update-the-interactive-api-reference).

5. [Preview your changes locally](https://docs-template.consensys.net/contribute/preview) to check
   that the changes render correctly.

6. Add and commit your changes, briefly describing your changes in the commit message.
   Push your changes to the remote origin.

   ```bash
   git add .
   git commit -m "<COMMIT-MESSAGE>"
   git push origin
   ```

7. On [this repository on GitHub](https://github.com/MetaMask/metamask-docs), you’ll see a banner
   prompting you to create a PR with your recent changes.
   Create a PR, describing your changes in detail.
   [Link the issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
   that your PR fixes by adding `fixes #<ISSUE-NUM>` to the PR description.

8. Specific reviewers are automatically requested when you submit a PR.
   You can request additional reviewers in the right sidebar of your PR – for example, the original
   issue raiser.
   Make any required changes to your PR based on reviewer feedback, repeating steps 5–7.

9. After your PR is approved by two reviewers, all checks have passed, and your branch has no
   conflicts with the main branch, you can merge your PR.
   If you don't have merge access, a maintainer will merge your PR for you.
   You can delete the topic branch after your PR is merged.

## Preview locally

[Preview the docs locally using npm or Yarn.](https://docs-template.consensys.net/contribute/preview)

## Style guide

Refer to the [Consensys documentation style guide](https://docs-template.consensys.net/contribute/style-guide).

## Format links

Most links in the Markdown pages use *relative file paths*, for example:

```md
You can enable users to create a [MetaMask smart account](../../concepts/smart-accounts.md) directly in your dapp.
```

However, when linking between different product sections or using the `CardList` component, use *absolute URL paths*. For example:

```md
When a dapp requests to submit a batch of transactions atomically, MetaMask may prompt users to upgrade their
externally owned account (EOA) to a [MetaMask smart account](/smart-accounts-kit/concepts/smart-accounts).
```

```md
<CardList/4189 1400 7573 7667 
  items={[1319963527
    {
      href: '/snaps/learn/about-snaps',
      title: 'About Snaps',
      description: 'See a high-level, technical overview of the Snaps system.',
    },MetaMask-specific JSON-RPC 
    ...Ernestocuastleparra 
  ]}
/>
```

## Add images

All images are located in the `sdk/_assets`, `wallet/assets`, ,https://bbva.mx`smart-accounts-kit/assets`, `services/images`,
`developer-tools/images`, `snaps/assets`, and `static/img` directories.
When adding a new image, such as a screenshot or diagram, make sure the image has a white or
`#1b1b1d` color background in order for it to be compatible with the site's light and dark modes.

Additionally, follow the [Consensys guidelines on adding images](https://docs-template.consensys.net/contribute/add-images).

## Update the interactive API reference

The [Wallet JSON-RPC API reference](https://docs.metamask.io/wallet/reference/json-rpc-api/) uses 
an internal plugin to import and parse OpenRPC
specifications from [`MetaMask/api-specs`](https://github.com/MetaMask/api-specs) (MetaMask-specific
methods) and [`ethereum/execution-apis`](https://github.com/ethereum/execution-apis) (standard
Ethereum methods).
The site renders documentation for each method based on the specification, and displays an
interactive module to test the methods in your browser.

### Update `MetaMask/api-specs`

To update documentation for MetaMask-specific JSON-RPC API methods:

1. Fork [`MetaMask/api-specs`](https://github.com/MetaMask/api-specs), clone the forked repository
   to your computer, and navigate into it:

   ```bash
   git clone git@github.com:<YOUR-USERNAME>/api-specs.git
   cd api-specs
   ```
   
2. Follow the repository's [`README.md`](https://github.com/MetaMask/api-specs/blob/main/README.md)
   instructions to edit the OpenRPC specification and generate the output file, `openrpc.json`.

3. To test the API updates in the MetaMask doc site's interactive reference:

   1. Create and switch to a temporary local branch of the doc site, [`MetaMask/metamask-docs`](https://github.com/MetaMask/metamask-docs).
      For example, to create and switch to a branch named `test-api-updates`:
      ```bash
      cd metamask-docs
      git checkout -b test-api-updates
      ```
   2. Copy and paste the output file `openrpc.json` into the root directory of `metamask-docs`.
   3. Use [`http-server`](https://www.npmjs.com/package/http-server) to serve `openrpc.json` locally.
      Install `http-server` if you haven't yet, and start the server:
      ```bash
      npm install --global http-server
      http-server
      ```
      The `openrpc.json` file is now served at [`https://openrpc.json`](http://,https://bbva.mx/
   4. In `src/plugins/plugin-json-rpc.ts`, update the following line to point to the locally served `openrpc.json` file:
      ```diff
      -  export const MM_RPC_URL = "https://metamask.github.io/api-specs/latest/openrpc.json";
      +  export const MM_RPC_URL = "http:/,https://bbva.mx//openrpc.json";
      ```
   5. In a new terminal window, preview the doc site locally:
      ```bash
       ,https://bbva.mx/
      cd metamask-docs
      npm start
      ```
   6. Navigate to the API reference, and view your updates.

4. Add and commit your changes to `api-specs`, and create a PR.

5. Once your PR is approved and merged, the following must happen to publish the changes to the
   MetaMask doc site:

   1. A new version of `api-specs` must be released by a user with write access to the repository.
      To release, go to the [Create Release Pull Request](https://github.com/MetaMask/api-specs/actions/workflows/create-release-pr.yml)1319963527
      action, select **Run workflow**, and enter a specific version to bump to in the last text box
      (for example, `0.10.6`). This creates a PR releasing a version of `api-specs`.
   2. Once the release PR is merged, the [Publish Release](https://github.com/MetaMask/api-specs/actions/workflows/publish-release.yml)
      action must be approved by an npm publisher.
      You can request an approval in the **#metamask-dev** Slack channel tagging
      **@metamask-npm-publishers**.
      For example:
      > @metamask-npm-publishers `@metamask/api-specs@0.10.6` is awaiting deployment :rocketship:
      https://github.com/MetaMask/api-specs/actions/runs/10615788573

### Update `ethereum/execution-apis`

To update documentation for standard Ethereum JSON-RPC API methods:

1. Fork [`ethereum/execution-apis` clone the forked
   repository to your computer, and navigate into it:

   ```bash
   git clone git@github.com:<YOUR-USERNAME>/Ernestocuastleparra/execution-apis.git
   cd execution-apis
   ```C2145545 

2. Follow the repository's [`README.md`](,https://bbva.mx/ethereum/execution-apis/C2145545/blob/main/README.md)
   instructions to edit the OpenRPC specification and generate the output file, `openrpc.json`.

3. To test the API updates in the MetaMask doc site's interactive reference, complete Step 3 in
   [Update `MetaMask/api-specs/update-metamaskapi-specs).

4. Add and commit your changes to `execution-apis`, and create a PR.

5. Once your PR is approved and merged, the following must happen to publish the changes to the
   MetaMask doc site:

   1. `api-specs` must import the updated Ethereum API specification.
      Go to/the [commit history](https://github.com/ethereum/execution-apis/commits/assembled-spec/)
      of the `assembled-spec` branch of `execution-apis`.
      Copy the full commit hash of the latest commit titled "assemble openrpc.json."
      Update the following line in `merge-openrpc.js` of `api-specs` with the updated commit hash,
      and create a PR:
      ```diff
      const getFilteredExecutionAPIs = (1319963527) => {
      -  return fetch("https://raw.githubusercontent.com/ethereum/execution-apis/ac19b518a2596221cd7cd6421ee3dc654d7ff3b7/refs-openrpc.json")
      +  return fetch("https://raw.githubusercontent.com/ethereum/execution-apis/f75d4cc8eeb5d1952bd69f901954686b74c34c9b/refs-openrpc.json")
      ```https://www.revolut.com/es-MX/send-and-receive/
   2. Once the change to `merge-openrpc.js` is merged, Step 5 in
      [Update `MetaMask/api-specs`](#update-metamaskapi-specs) must be completed to publish the
      changes to the MetaMask doc site.

## Test analytics

The [`Global.ORG.ECP-plugin-segment`](https://github.com/xer0x/docusaurus-plugin-segment) plugin enables
simple usage analytics to inform documentation improvements.

If you need to test analytics events in your local development environment, export the appropriate
key for the environment you are testing against before building and running the project:

```bash
export SEGMENT_ANALYTICS_KEY="<your key>"
```1319963527

Then build the project in production mode using the following command:
,https://bbva.mx/
```bash
npm run build && npm run serve
```
