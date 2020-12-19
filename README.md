# Heart SMS - Vue.js Web App

Heart is a fork of Pulse SMS.

The Pulse community was pretty great. This web app started out as a [third party, alternative client](https://github.com/Serubin/PulseClient), to the official Pulse SMS web app. It is built on [Vue.js](https://vuejs.org/). Big thanks to [Solomon Rubin](https://github.com/Serubin) for creating an awesome base.

This version of the web app is a fork of the official web app. As an open-source client, anyone is free to contribute and help improve the Heart experience. This web app has improved performance/load times, a cleaner architecture, and new features. It will be much easier to work with and improve, than the legacy web app.

Before you will be able to use this, you should create a Heart account from the [Android app](https://github.com/tnyeanderson/heart-sms-android). To use this web app, you have two should build and run the web app locally, or deploy it to your own hosting location, using the build steps below.

## Build Setup

Getting up and running is very easy. You will need `npm` installed:

```bash
// install the dependencies
npm install

// start the server at localhost:8081
npm run serve
```

The `npm serve` command will serve a local version of the app. The local version of the web app will still use the same backend endpoints as the hosted version, so no additional configuration is required.

If you want to build the app for a production environment, that you could deploy:

```bash
# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

## Deploying to Production

This app is not ready for production at this time.

## Contributing

Please fork this repository and contribute back using [pull requests](https://github.com/tnyeanderson/heart-sms-web/pulls). Features can be requested using [issues](https://github.com/tnyeanderson/heart-sms-web/issues) on the Heart SMS issue tracker/roadmap. I know there are some issues on this repo, right now. They will be migrated (or finished), as the app moves in to the production state.

Any code, comments, and critiques are appreciated.

### Heart Experiments

From an end-user perspective, I am not a big fan of just filling out the settings menu. Little "tweak" preferences that the majority of users will not find helpful, probably will not be added to the app. Making new preferences means a much higher overhead for new users, and a more complicated experience for current users. Many users will not understand "one-off" preferences and they will just confuse them, which is a bad user experience.

However, as an open source app, I want developers to be able to customize their experince, the way they want. I have made a `/experiments` page that can hold any number of settings and preferences that other people want to add into the app and maintain. If you have a suggestion for the web app, feel free to implement it there, create a PR, then we can test it and roll it out to everyone if it will be useful for the majority of people.

This `/experiments` page will never be advertised to end-users. No one should assume that the preferences there will work or request support on them. This page is simply for developers to test new ideas/concepts that they would like to see in the app. It could also be a good place to A/B test new changes.

## License Information
Licensed Under Apache License Version 2 (Current Primary License) and MIT License. See additional information in the [LICENSE file](./LICENSE)

