<sup>BD 2025</sup>

# Example services
### What is this?
A collection of example services (which came from my [now-defunct fork of ActivityPods](https://github.com/briidee3/activitypods/) when I integrated the backend of Memory directly into the ActivityPods backend) demonstrating how one can connect the frontend and backend via calls to REST API(s) put up by RedPanda (RP) and/or OpenSearch (OS).

### `emit-public.js`
- Example service/handler for automatic sending of public activities to the RP REST API whenever someone on this instance of the app (i.e. Memory) uploads a public post

### `opensearch.js`
- Example service/handler which puts up a REST API for the POD provider at `<website-ip>/`, `<website-ip>/tags`, and `<websie-ip>/tags/<tag>`, as well as automatic handling and use of the `search_after` parameter of OpenSearch for use in pagination of the results

### `redpanda.js`
- Example service/handler for use authenticating and communicating with an instance of RedPanda at the set address
