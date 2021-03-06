# Site/App Data

> Tips of using `YAML` and `JSON` to seperate out data from our code.

While this can be done in a `JSON` file and it seems to be more common, I prefer to use
YAML because of how clean and easy it write and read it is.

By using `js-yaml-loader`, it gets imported as JS which is exactly how JSON is
imported by Webpack.

There are many use cases and this is just one of them show below to illustrate
the concept.

## Example

**`db/site.yaml`**

```yaml
nav:
  - title: Home
    path: /

  - title: About
    path: /about

  - title: Contact
    path: /contact
```

**`nuxt.config.js`**

```js
export default {
  build: {
    extend(config, ctx) {
      config.module.rules.push({
        test: /\.ya?ml$/,
        use: "js-yaml-loader"
      })
    }
  }
}
```

**`store/index.js`**

```js
import siteData from "@/db/site.yml"

export const state = () => ({
  nav: siteData.nav
})
```
