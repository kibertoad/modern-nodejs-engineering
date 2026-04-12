See TECH_STACK.md for the tech stack used in this project.

All of the homework assignments need to be split into pull requests, each pull request only covering a single phase of the homework assignments. 

Since every homework assignment is based on everything that was done before, you can branch out incrementally so that every subsequent pull request would contain changes in every previous pull request.

Please merge a pull request after it was graded.

Pull request 1:

* Create a fastify application for a pizza production backend service;
* Create a healthcheck controller that returns 'OK' text response;
* Create pizza ingredients stock management controller that receives request with a body that provides details of a received ingredient shipment
* Implement validation for the request body, using one of the following:
  * [Built-in Fastify validator](https://fastify.dev/docs/latest/Reference/Validation-and-Serialization/);
  * [Zod](https://zod.dev/);
  * [fastify-typeprovider-zod](https://github.com/turkerdev/fastify-type-provider-zod) -> BONUS POINTS;
  * [fastify-api-contracts](https://github.com/lokalise/shared-ts-libs/tree/main/packages/app/fastify-api-contracts) -> BONUS POINTS.
* Implement an automated test (see USEFUL_REFERENCES.md for some tips) that makes requests to the stock management endpoint, cover the following scenarios:
  * 400 response to an invalid request;
  * 200 response to a valid request;

Pull request 2:
* Create ShipmentService for your application, which implements `registerShipment` method, that needs to include the following logic, using the Strategy pattern (https://refactoring.guru/design-patterns/strategy), and expecting the following parameters: targetWarehouse (string), ingredients (id: string, units: number) - array:
  * If ingredient shipment is submitted out of the working hours for the target warehouse, reject it;
  * If ingredient shipment has less than minimum amount of units of the warehouse, reject it;
  * If ingredient shipment has more than maximum amount of units for the warehouse, split it into multiple shipments of up to 1000 units (see [USEFUL_ALGORITHMS.md](./USEFUL_ALGORITHMS.md) for a splitting algorithm);
  * Support multiple warehouses with different working hours and minimum and maximum amounts of units.
* Implement tests that validate all of the rules for the service;
* Implement persistence layer with drizzle (https://orm.drizzle.team/docs/get-started/postgresql-new):
  * Create drizzle configuration file;
  * Create drizzle table schema definition file;
  * Generate migrations from schema definition file;
  * Run migrations on a PostgreSQL instance (from Docker or locally installed)
    * Docker: https://docs.docker.com/desktop/setup/install/windows-install/ / https://docs.docker.com/desktop/setup/install/mac-install/
    * Direct PostgreSQL installation: https://www.postgresql.org/download/
  * Create a repository that implements the following methods:
    * `createShipment` method;
    * `getShipmentById` method;
    * `getAllShipments` method;
    * `deleteShipment` method;
  * Implement tests for all the methods
  * Adjust service to use the repository for creating shipments.

Grading details for pull request 2: 
  * 6 points: service and one business rule are implemented. repository is implemented with in-memory storage without drizzle
  * 8 points: service, all business rules and multi-warehouse support are implemented. repository is implemented with in-memory storage without drizzle
  * 10 points: service, all business rules and multi-warehouse support are implemented. repository is implemented with PostgreSQL storage using drizzle (or kysely)
