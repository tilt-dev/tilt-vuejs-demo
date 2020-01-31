# Demo Vue.js app with Tilt

This is a demo Vue.js app showing how to do frontend development in a local Kubernetes environment with [Tilt](https://tilt.dev/).

This [docs page](https://docs.tilt.dev/nodejs_microservice_hotreloading.html) provides additional context for hot reloading in Tilt, as well as a walkthrough of a [demo React app using Tilt](https://github.com/windmilleng/tilt-frontend-demo). This project is similar, but for folks interested in using Vue.js instead.

This project was bootstrapped with [Vue CLI](https://cli.vuejs.org/).

## Instructions

- Install [Tilt](https://tilt.dev/) and a [local Kubernetes environment](https://docs.tilt.dev/choosing_clusters.html).
- Optional: Read the beginner [Tilt tutorial](https://docs.tilt.dev/tutorial.html).
- With the local Kubernetes environment running, `cd` into the root directory of this project, and run `tilt up`.
- Navigate to [http://localhost:8080/](http://localhost:8080/) in your browser.
- Make any changes to the app, such as saving new text in [HelloWorld.vue](src/components/HelloWorld.vue). 
- Observe the changes reflected immediately in your browser, without refreshing.

## Dockerfile

The [Dockerfile](Dockerfile) contains `npm run serve`, thus running a dev server within the container used by Kubernetes. Tilt uses [live_update](https://docs.tilt.dev/live_update_tutorial.html) (as specified in the [Tiltfile](Tiltfile)) to dynamically inject changes into the container, as you make them, allowing you a realtime frontend development experience, similar to as if you were running the app directly locally. In production, you _should not_ use `npm run serve` in the container, but build the app instead. See [examples of this in the Vue.js Cookbook](https://vuejs.org/v2/cookbook/dockerize-vuejs-app.html).
