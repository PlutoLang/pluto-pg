# pluto-pg 
Postgres wire protocol client library written in Pluto, including SASL SCRAM algorithm.

## Usage Example
```lua
require "pg"
local s = require"socket".connect("localhost", 5432)
pgauth(s, "pg", "pg", "test") -- user, pass, db
while pgrecv(s) ~= "Z" do end -- Await ReadyForQuery
print(dumpvar(pgquery(s, [[SELECT * FROM "test" LIMIT $1]], 1)))
```
