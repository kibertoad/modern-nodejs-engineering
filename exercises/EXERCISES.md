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

Exercise 2:
  * Create OrderService for your application, which implements `placeOrder` method, which needs to include the following logic, using the Strategy pattern (https://refactoring.guru/design-patterns/strategy):
    * If order is submitted out of the working hours, reject it;
    * If order is submitted out of peak hours, apply Y% (specific to country) discount;
    * Ir order is above X EUR (specific to country) total cost, apply Y% (specific to country) discount 
    * In case several discounts are applied, the larger one wins, they are not summed.
    * Support multiple countries with different working hours and discount thresholds and sizes.
  * Implement tests that validate all of the rules for the service;
  * Implement persistence layer with drizzle (https://orm.drizzle.team/docs/get-started/postgresql-new):
    * Create drizzle configuration file;
    * Create drizzle table schema definition file;
    * Generate migrations from schema definition file;
    * Run migrations on a PostgreSQL instance (from Docker or locally installed)
      * Docker: https://docs.docker.com/desktop/setup/install/windows-install/ / https://docs.docker.com/desktop/setup/install/mac-install/
      * Direct PostgreSQL installation: https://www.postgresql.org/download/
    * Create a repository that implements the following methods:
      * `createOrder` method;
      * `getOrderById` method;
      * `getAllOrders` method;
      * `deleteOrder` method;
    * Implement tests for all the methods
    * Adjust service to use the repository for creating orders.

Exercise 3:
  * Create an API contract for Shipment Service, which specified retrieving an amount of a specific type of ingredient currently available in the warehouse.
  * Implement a new Shipment Service endpoint, utilizing the API contract, for providing the ingredient availability.
  * Implement a call from Order Service to Shipment Service for checking the ingredient availability, using the API contract.
