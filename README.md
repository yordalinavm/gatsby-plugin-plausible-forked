# @devular/gatsby-plugin-plausible

This plugin was forked from [pixelplicity/gatsby-plugin-plausible](https://github.com/pixelplicity/gatsby-plugin-plausible) to support Plausible's proxying configuration.

[![npm package](https://flat.badgen.net/npm/v/gatsby-plugin-plausible)](https://badgen.net/npm/v/gatsby-plugin-plausible)

A Gatsby plugin for adding [Plausible](https://plausible.io/) analytics to your Gatsby site.

The plugin includes the Plausible tracking script. It supports using a custom domain and excluding specific paths from recording page views.

---

- [Install](#install)
  - [Manual](#manual)
  - [Gatsby Recipe](#gatsby-recipe)
- [How to use](#how-to-use)
  - [Options](#options)
  - [Pageview events](#pageview-events)
  - [Triggering custom events](#triggering-custom-events)
- [Changelog](#changelog)
- [License](#license)

## Install

### Manual

1. Install `@devular.gatsby-plugin-plausible`

   `npm install --save @devular/gatsby-plugin-plausible`

2. Add plugin to `gatsby-config.js`

   ```javascript
   // In your gatsby-config.js
   module.exports = {
     plugins: [
       // The only required option is the domain
       {
         resolve: `@devular/gatsby-plugin-plausible`,
         options: {
           domain: `your-site.com`,
           proxyScript: `/sub-directory/script.js`,
           proxyApi: `/sub-directory/api/event`,
         },
       },
     ],
   };
   ```

### Gatsby Recipe

This will install `@devular/gatsby-plugin-plausible` and add a sample configuration.

1. Upgrade gatsby-cli and gatsby to the latest version:

   `npm install -g gatsby-cli@latest`
   `npm install gatsby@latest`

2. Run the recipe
   `gatsby recipes https://raw.githubusercontent.com/devular/gatsby-plugin-plausible/master/gatsby-recipe-plausible.mdx`

3. Update `gatsby-config.js` [options](#options).

To read more about recipes check out the [announcement](https://www.gatsbyjs.org/blog/2020-04-15-announcing-gatsby-recipes/).

## How to use

_NOTE: By default, this plugin only generates output when run in production mode. To test your tracking code, run `gatsby build && gatsby serve`_.

### Options

| Option         | Explanation                                          |
| -------------- | ---------------------------------------------------- |
| `domain`       | The domain configured in Plausible (required)        |
| `proxyScript`  | A script location for a proxy configuration          |
| `proxyApi`     | An collection endpoint for aproxy configurations     |
| `excludePaths` | Array of pathnames where page views will not be sent |

\_NOTE: You can [read more about proxying Plausible here](https://plausible.io/docs/proxy/introduction)

### Pageview events

Pageviews are sent automatically when a user changes routes, including the initial load of your site.

### Triggering custom events

To track goals and conversions you have to trigger custom events first.

```js
window.plausible('Signup', {
  callback: () => console.info('Sent Signup event'),
});
```

The event name can be anything. The second argument is an object with options. The only supported option is `callback` that is called once the event has been sent.

_NOTE: Custom events will not show up right away. You have to configure a goal in your Plausible dashboard_.

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](https://github.com/devular/gatsby-plugin-plausible/blob/master/LICENSE) | [Devular](https://devular.com)

Forked from: https://github.com/pixelplicity/gatsby-plugin-plausible with [MIT](https://github.com/pixelplicity/gatsby-plugin-plausible/blob/master/LICENSE)
