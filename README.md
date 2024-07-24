# LiveMaps

To start your Phoenix server:

  * Install dependencies with `mix deps.get`
  * Start Phoenix endpoint with `mix phx.server` or inside IEx with `iex -S mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

1. Design Decisions
Framework Choice using phoenix. why?Because it's scale without compromising the development speed. and many code tools decrease the javascript thickness
Architecture: 
         +-------------------------+
         |                         |
         |       Client            |
         |                         |
         +-----------+-------------+
                     |
                     v
         +-----------+-------------+
         |                         |
         |       Endpoint          |
         |                         |
         +-----------+-------------+
                     |
                     v
         +-----------+-------------+
         |                         |
         |        Router           |
         |                         |
         +-----------+-------------+
                     |
         +-----------+-------------+
         |           |             |
         v           v             v
+--------+---+   +---+--------+   +----------+
| Controller |   |  Channel   |   |  Context  |
+-------+----+   +----+-------+   +-----+----+
        |             |                |
        v             v                v
  +-----+----+   +----+-----+     +----+-----+
  |   View    |   |  PubSub  |     |  Schema  |
  +-----+----+   +----+-----+     +----+-----+
        |             |                |
        v             v                v
  +-----+----+   +----+-----+     +----+-----+
  | Template |   |  Clients  |     | Database |
  +----------+   +-----------+     +----------+
This diagram represents the flow of a typical request:

* The client makes a request to the endpoint.
* The router directs the request to the appropriate controller.
* The controller interacts with the context to fetch or manipulate data.
* The context communicates with the schema to access the database.
* The controller renders a view, which uses a template to generate the HTML.
* The response is sent back to the client.

2. Testing Strategy
Types of Tests: Discuss the types of tests implemented (unit tests, integration tests, end-to-end tests, etc.).
Tools Used: 
The setup, here are some tools:
1. ExUnit:
* The built-in testing framework for Elixir.
* Automatically included in Elixir projects.
* No need to add it explicitly in mix.exs.
2. ExMachina:
* A library for creating test data.
* Useful for setting up factories.
* Example dependency: {:ex_machina, "~> 2.7", only: :test}
3. ExCoveralls:
* A tool for tracking test coverage.
* Example dependency: {:excoveralls, "~> 0.10", only: :test}
4. Mocking Libraries:
* Libraries like Mox for creating mocks and stubs.
* Example dependency: {:mox, "~> 1.0", only: :test}

3. Issues Encountered
Common Issues: 
* Issues Encountered and Solutions
* Flaky Tests: Tests that sometimes pass and sometimes fail.
* Solution: Ensure tests are isolated, use mocks/stubs for external dependencies.
* Slow Test Suite: Long-running tests due to integration or end-to-end tests.
* Solution: Optimize test setup, parallelize tests, and use faster test data factories.
* Technical Challenges: Describe any significant technical challenges and the solutions implemented.
# mapSearch
