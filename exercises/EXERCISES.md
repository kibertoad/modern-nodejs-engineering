See TECH_STACK.md for the tech stack used in this project.

Exercise 1:

* Create a fastify application for a pizza ordering backend service;
* Create a healthcheck controller that returns 'OK' text response;
* Create pizza ordering controller that receives request with a body that provides details of a received pizza order
* Implement validation for the request body, using one of the following:
  * [Built-in Fastify validator](https://fastify.dev/docs/latest/Reference/Validation-and-Serialization/);
  * [Zod](https://zod.dev/);
  * [fastify-typeprovider-zod](https://github.com/turkerdev/fastify-type-provider-zod) -> BONUS POINTS;
  * [fastify-api-contracts](https://github.com/lokalise/shared-ts-libs/tree/main/packages/app/fastify-api-contracts) -> BONUS POINTS.
* Implement an automated test (see USEFUL_REFERENCES.md for some tips) that makes requests to the stock management endpoint, cover the following scenarios:
  * 400 response to an invalid request;
  * 200 response to a valid request;
