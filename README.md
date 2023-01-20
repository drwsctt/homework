cd to directory and run 'docker compose up' to start the web and redis services.

Add something to the redis cache via the add_to_cache API, which returns a unix timestamp as a unique UUID:

$ curl http://localhost:4195/add_to_cache/post -d "Hmm, I think this works."

1674186332392802914


To verify the payload, use the get_from_cache API with the UUID you just received:

$ curl http://localhost:4195/get_from_cache/post -d "1674186332392802914"

Hmm, I think this works.


For debugging, redis ports are open too, and you can run redis-cli to verify:

$ redis-cli

127.0.0.1:6379> keys *

1) "1674186332392802914"

127.0.0.1:6379> get 1674186332392802914

"Hmm, I think this works."
