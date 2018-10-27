# SearchHero
### _A sieve-like query builder for persistent and evolving searches of arbitrary data sources_

We create an intermediate interface between the client initiating a query and the "upstream" service(s) or database(s) they are querying against.  We cache the query supplied by the client and select and record the search space it is applied to, so as to iteravely retrieve smaller amounts of data which may be more easily processed/displayed by the client.

Knowing what has been queried, and over which areas of the search space, enables a several key features:
 * The load and traffic of the data source _may_ be reduced as it processes greater, yet simpler, queries which scan narrower portions of the database.
 * In no case does the client retrieve the same data twice, because we supply only the un-queried portions of the search space to the upstream data source.
 * The client can iteravely modify their query arbitrarily; we simply perform a differential between current and previous queries applicable to the search space to retrieve data that matches the current query and has not been retrieved in previous iterations.

See US Patent #10127286 and https://auctionhero.io/ for an embodiment.
