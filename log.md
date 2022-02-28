# 100 Days Of Code - Log

### Day 1: December 31, 2021

**Today's Progress**: Started a golang cobra CLI for icanhazdadjoke

**Thoughts:** I completed the tutorials [Part 1](https://dev.to/divrhino/building-a-command-line-tool-with-go-and-cobra-3mjd) and [Part 2](https://dev.to/divrhino/adding-flags-to-a-command-line-tool-built-with-go-and-cobra-34f1) using cobra and golang to call the icanhazdadjoke REST API. Icanhazdadjoke has a GraphQL API, tomorrow I will converting my app to call the GraphQL implementation

**Link(s) to work**: 

* [DadJoke CLI](https://github.com/cryanbrow/dadjoke)

--- 
### Day 2: January 1, 2022

**Today's Progress**: Added Unit tests to the dad joke CLI, mocked out the calls to the back end service.

**Thoughts:** I struggled a lot at the beginning of this. Mocking in Go is significantly more complicated than in Java with annotations. You have to create an interface for a class that already exists and then pass in a reference to the library in an init method. This init method happens before any other code execution so when you load in a Mock in your test doing the same thing it replaces what is already there. It makes sense now that I understand what's going on. It's just really quite complex for something that is rather easy in Java.

**Link(s) to work**: 

* [DadJoke CLI](https://github.com/cryanbrow/dadjoke)

**Links to references used**:

1. [Mocking Guide](https://levelup.gitconnected.com/mocking-outbound-http-calls-in-golang-9e5a044c2555)
2. [Unit Tests](https://www.digitalocean.com/community/tutorials/how-to-write-unit-tests-in-go-using-go-test-and-the-testing-package) 

--- 
### Day 3: January 2, 2022

**Today's Progress**: Created my Eve Online graphql server from my graphql schema I had built in the past.

**Thoughts:** cqlgen is a life saver. The fact that it builds out your objects from your schema and sets up resolvers and everything. It's just incredible. The task of building resolvers is still going to be daunting for a schema the size of the one that I have but it will be fun. I don't know how unit testing for generated code works. I don't know if the best approach would be to ignore it? Feels like unit testing generated code is chasing a moving target. I'll search around tomorrow and see what people say.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [cqlgen guide](https://gqlgen.com/getting-started/)
2. [appending to slices](https://go.dev/tour/moretypes/15) 

--- 
### Day 4: January 3, 2022

**Today's Progress**: I converted my schema over to snake case and implemented the ordersForRegion resolver.

**Thoughts:** With the json implementation in the auto generated go code wanting snake case and me not wanting to modify the finals every time I built them I updated the schema. I created a resolver that only pulls the first page but that works for now. Next is caching.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [int to string](https://golang.cafe/blog/golang-int-to-string-conversion-example.html)

--- 
### Day 5: January 4, 2022

**Today's Progress**: I added a data access layer, iterated through pages, learned url.URL for building dynamic urls and struggled conditional statements.

**Thoughts:** It's really important to not overlook a != and mistake it for a ==. That cost me like 15 minutes of my life. url.URL makes calling APIs so much easier, I'm glad I took the time to do it instead of just concatenating strings.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [slice append](https://yourbasic.org/golang/append-explained/)
2. [for loop](https://yourbasic.org/golang/for-loop/)
3. [URL buildup](https://pkg.go.dev/net/url#URL)
4. [query resolvers](https://gqlgen.com/reference/resolvers/)

--- 
### Day 6: January 5, 2022

**Today's Progress**: Today was a throwaway. I implemented a resolver for systembyid but all the other work I did, did not accomplish much. ESI for EVE was down so I could test my new resolver.

**Thoughts:** The Star Wars example generates their resolvers from the schema. I really want this and for the life of me I can't figure out why mine don't. I added a couple of lines to my resolver to generate easily every time so that's nice at least.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [star wars example](https://github.com/99designs/gqlgen/tree/master/example/starwars)
2. [getting started](https://gqlgen.com/getting-started/)

--- 
### Day 7: January 6, 2022

**Today's Progress**: Figured out all of yesterdays issues and got a resolver going for the Systems within Order so that's exciting. My first nested type.

**Thoughts:** The missing piece was capitalization on my types in the schema and matching properties in the gqlgen. Also really cemented in what the parens before a method name are for. It's for defining methods for a struct with is handy. None of the Pluralsight courses I took really drove that home.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [methods](https://go.dev/tour/methods/1)
2. [eve swagger system by id](https://esi.evetech.net/ui/#/Universe/get_universe_systems_system_id)

--- 
### Day 8: January 7, 2022

**Today's Progress**: Today was just doing work. Didn't have to figure out much but accomplished an absolute ton. Got like 6-7 resolvers and dao endpoints built.

**Thoughts:** Today was just a day of doing.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [voyager](https://apis.guru/graphql-voyager/)

--- 
### Day 9: January 8, 2022

**Today's Progress**: Today was another day of just writing resolvers and endpoints into the ESI. Got a heck of a lot done though.

**Thoughts:** Today was just a day of doing. Created my first custom error though so that was fun.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [errors](https://yourbasic.org/golang/create-error/)

--- 
### Day 10: January 9, 2022

**Today's Progress**: Huge day today. I decided I wanted to increase the performance so I implemented an in memory cache for one of the API endpoints. I implemented in a way so it's agnostic to the data that is coming in which will make it super reusable.

**Thoughts:** Implemented a cache with a map to start with and ran into concurrent modification exceptions. Found sync.map and it was just what I needed. Turned out great. So now I'm caching things with expiry timestamps and everything. It's super fun.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [maps](https://medium.com/@luanrubensf/concurrent-map-access-in-go-a6a733c5ffd1)
2. [sync.map](https://pkg.go.dev/sync#Map)
3. [medium sync.map](https://medium.com/@deckarep/the-new-kid-in-town-gos-sync-map-de24a6bf7c2c)

--- 
### Day 11: January 10, 2022

**Today's Progress**: Another great day. I learned how to embed a React app in my go app so I was able to put Voyager in my app as a separate endpoint to call. I added caching to everything and I built a couple of new resolvers.

**Thoughts:** Implementing Voyager was immensely easy. In fact putting web apps in your go app is absurdly easy. Makes me think about a whole mess of helper utilities that I could put in go apps really easily.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [voyager example](https://github.com/APIs-guru/graphql-voyager/blob/master/example/index.html)
2. [embed app](https://www.fareez.info/blog/embedding-react-app-in-go-binary/) - Didn't work but if it does it's a far cleaner implementation.
3. [embed app long](https://blog.jetbrains.com/go/2021/06/09/how-to-use-go-embed-in-go-1-16/) - Worked but is a lot of code.

--- 
### Day 12: January 11, 2022

**Today's Progress**: I pulled out the REST logic into it's own method and replaced it all calls. Also did a pretty big logging overhaul. Learned how to implemented JSON fields in logs.

**Thoughts:** Really thought I broke almost everything. But managed to bring it back around. Learned why it's important to know that := is not the same as =.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [logrus](https://github.com/sirupsen/logrus)
2. [logging best practices](https://qvault.io/golang/golang-logging-best-practices/)

--- 
### Day 13: January 12, 2022

**Today's Progress**: I cleaned up my logging. Almost fully converted to JSON logging at this point. I also implemented a Redis cache instead of an in memory cache in a map. It was surprisingly simple to do. I'm running it on the linux subsystem on my Windows machine in the interim while I build out my home lab.

**Thoughts:** Redis sure is nice.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [redis install](https://redis.io/download)
2. [redis ttl](https://redis.io/commands/TTL)
3. [redis go](https://github.com/go-redis/redis)
4. [go byte array to string](https://yourbasic.org/golang/convert-string-to-byte-slice/)

--- 
### Day 14: January 13, 2022

**Today's Progress**: I fixed an issue where an http response returning no error but a non 200 response code was being stored to Redis. I also added a Corporation resolver and worked on the schema and some more endpoints for the ESI endpoints.

**Thoughts:** After a 5 hour drive today it was nice to just do something easy.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [caldari navy killboard](https://zkillboard.com/corporation/1000035/)

--- 
### Day 15: January 14, 2022

**Today's Progress**: I built two resolvers, one for corporatins and one for factions. The faction endpoint on the ESI was a get all so I had to iterate through the response and cache the pieces individually. Will be a super helpful thing to follow as their are a great many endpoints like that.

**Thoughts:** Make sure you flushall Redis keys after making a schema addition or you'll wonder why that key keeps coming back null.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [json marshalling](https://pkg.go.dev/encoding/json#Marshal)
2. [for each loop](https://yourbasic.org/golang/for-loop/)

--- 
### Day 16: January 15, 2022

**Today's Progress**: I flushed out about 10 resolvers and added like 5 REST dao endpoints.

**Thoughts:** Got some good work done today

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [graphql schema](https://graphql.org/learn/schema/)

--- 
### Day 17: January 16, 2022

**Today's Progress**: Worked on more resolvers and CREST endpoints. Getting close to flushing most everything that I have defined in the schema out.

**Thoughts:** Getting close to the end of this.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [graphql schema](https://graphql.org/learn/schema/)

--- 
### Day 18: January 17, 2022

**Today's Progress**: Finished out all the schema I had defined. Started adding comments to the schema for intuitive descriptions of fields.

**Thoughts:** Writing useful comments is always the hardest part.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [schema comments pull request](https://github.com/99designs/gqlgen/pull/320)

--- 
### Day 19: January 18, 2022

**Today's Progress**: Added a Dockerfile for building a docker image. Reverted to the memory cache as installing Docker Desktop broke networking to the Windows subsystem for linux.

**Thoughts:** Don't know why I'm unable to access the Windows Subsystem for Linux. It won't matter soon as the home lab will be going soon and I'll host Redis on a server.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [golang docker app](https://codefresh.io/docs/docs/learn-by-example/golang/golang-hello-world/)

--- 
### Day 20: January 19, 2022

**Today's Progress**: I tried to get kubernetes running on my raspberry pis but couldn't get things to start. I installed Redis on a raspberry pi instead and pointed my app to that. I added documentation to another object. I built out the History endpoint. Finally I refactored the caching into its own package. 

**Thoughts:** I think to get Kubernetes running on my pis I will have to flash to use armhf

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [redis install](https://redis.io/download)

--- 
### Day 21: January 20, 2022

**Today's Progress**: I got 10 raspberry pis running today on POE on my Cisco switch. Just had to change the orientation of my header on the POE pins on the pi. I started implementing graphql queries by name instead of id which required a massive refactor. Got most of the way done with the refactor. Next is fully building out the endpoint.

**Thoughts:** Did a lot of learning today. My first switch statement. First HTTP Post. Struct to JSON to Byte Buffer.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [switch](https://gobyexample.com/switch)
2. [struct to byte buffer](https://gosamples.dev/struct-to-io-reader/)
3. [single item array](https://stackoverflow.com/questions/18906817/how-do-i-create-an-array-of-one-item-in-go/18906818)
4. [typed nil](https://stackoverflow.com/questions/19761393/why-does-go-have-typed-nil)

--- 
### Day 22: January 21, 2022

**Today's Progress**: I implemented a large refactor and allowed querying by name of orders and types. I also implemented the method to be easily expanded out to other endpoints as well.

**Thoughts:** Made a lot of patch cables today for the home lab. Excited to get things up and running from that perspective.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [constants](https://go.dev/tour/basics/15)
2. [empty string check](https://stackoverflow.com/questions/18594330/what-is-the-best-way-to-test-for-an-empty-string-in-go)
3. [test exclude files](https://stackoverflow.com/a/61604251)
4. [too many open files](http://woshub.com/too-many-open-files-error-linux/)

--- 
### Day 23: January 22, 2022

**Today's Progress**: Today was a day of days. I installed Ansible, ran an ansible playbook to install kubernetes on 10 raspberry pis, built yamls for redis on k8s, installed redis, exposed redis on the workers, connected to redis from my computer, built an image of eve-graphql for arm, installed it to k8s, and connected to redis on kubernetes.

**Thoughts:** I had a fantastic day of getting stuff accomplished. I think I want to look into using my Kemp Loadmaster tomorrow for creating loadbalancers for the cluster.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Redis Kube](https://github.com/cryanbrow/redis-kube)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [install helm](https://helm.sh/docs/intro/install/)
2. [k3s on raspberry pi](https://bryanbende.com/development/2021/05/07/k3s-raspberry-pi-initial-setup)
3. [different architecture docker build](https://stackoverflow.com/questions/60114854/pull-docker-image-for-different-architecture/60116565)
4. [multi-arch docker build](https://www.docker.com/blog/multi-arch-build-and-images-the-simple-way/)

--- 
### Day 24: January 23, 2022

**Today's Progress**: Implemented externalized config in my application by loading yamls. Implemented yaml config map in my helm chart as well.

**Thoughts:** After following Kelsey Hightower for so long it was cool to use his env config library.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [external config](https://dev.to/ilyakaznacheev/a-clean-way-to-pass-configs-in-a-go-application-1g64)
2. [external config github](https://github.com/amritsingh/golang_tutorials/tree/main/revel/config_to_yaml/app)
3. [env config](https://github.com/kelseyhightower/envconfig)
4. [init function progression](https://stackoverflow.com/questions/24790175/when-is-the-init-function-run)

--- 
### Day 25: January 24, 2022

**Today's Progress**: Attempted to parse an ISO 8601 timestamp from a header from http response to set a TTL in Redis.

**Thoughts:** Dealing with time is always a bear and this was no exception. An hour of coding and I'm not closer than I was.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [ISO 8601](https://stackoverflow.com/questions/38596079/how-do-i-parse-an-iso-8601-timestamp-in-go)
2. [int64 to string](https://yourbasic.org/golang/convert-int-to-string/)
3. [time format](https://gobyexample.com/time-formatting-parsing)

--- 
### Day 26: January 25, 2022

**Today's Progress**: Fixed my TTL bug. It was RFC1123. Started a massive refactor to potentially eliminate hundreds of lines of code. 

**Thoughts:** Genericizing methods is rough with there is like 30 use cases to check for.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

none

--- 
### Day 27: January 26, 2022

**Today's Progress**: Completed the refactor of removing caching and url logic from the service layer. Moved Asteroid Belts to the universe package.

**Thoughts:** Pretty good. I fought a ghost because I was seeing an empty array. I wonder if in graphql there is a way to hide objects whose all sub objects are nil or empty arrays

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [required graphql fields](https://graphql.org/learn/queries/)
2. [byte slice to string](https://yourbasic.org/golang/convert-string-to-byte-slice/)

--- 
### Day 28: January 27, 2022

**Today's Progress**: Completed refactor of data access layer into separate layers by ESI type.

**Thoughts:** Tomorrow I'm going to start working on unit testing. This will be fun.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

none

--- 
### Day 29: January 28, 2022

**Today's Progress**: I unit tested one file to 100% code coverage. 

**Thoughts:** I found out getting around using init in packages is rough when you need to override things within them. I'm not sure what I'll do in the future as the way I've done I don't particulary care for.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [coverage tool](https://gist.github.com/ammario/8e802dc0595faaed241bad19f72eda5c)
2. [test main](https://stackoverflow.com/questions/14249217/how-do-i-know-im-running-within-go-test)
3. [go pwd](https://gist.github.com/arxdsilva/4f73d6b89c9eac93d4ac887521121120)
4. [print time format](https://go-recipes.dev/parsing-and-displaying-time-with-go-a8ee85e23fff)
5. [time](https://gobyexample.com/time)

--- 
### Day 30: January 29, 2022

**Today's Progress**: I learned how to do functions that are directly tied to structs. This allowed me to refactor my redis caching.

**Thoughts:** I need to understand putting a struct before the method definition and what that allows for.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [http client](https://go.dev/src/net/http/client.go)

--- 
### Day 31: January 30, 2022

**Today's Progress**: I worked on adding unit test coverage.

**Thoughts:** I got a better grasp on interfaces and mocking but I don't full understand the rune thing that I ran into in the http library.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [interfaces](https://go.dev/doc/effective_go#interfaces)

--- 
### Day 32: January 31, 2022

**Today's Progress**: I attempted to exclude generated code from unit test coverage to get a better idea of where I am. I was not successful.

**Thoughts:** Part of me understands why they don't include a way to exclude packages from coverage but the other part of me finds it really frustrating when I'm trying to think through quality gates in the future.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [stack overflow exclude](https://stackoverflow.com/questions/55224561/how-to-exclude-or-skip-specific-directory-while-running-go-test)
2. [coverpkg exclude](https://liza.io/excluding-mocks-from-coverage-reports/)

--- 
### Day 33: February 1, 2022

**Today's Progress**: I finalized the commands to exclude generated code from the coverage report. I started to build out the tests for the dogma package.

**Thoughts:** Finally starting to understand mocking. Just takes a lot of repitition. 

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

none

--- 
### Day 34: February 2, 2022

**Today's Progress**: Built unit tests for the Dogma package. Integrated Github Actions for the project including building, testing, covering, and stashing reports.

**Thoughts:** Using Github Actions was so much eaiser than bulding Jenkins Pipelines.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [actions quickstart](https://docs.github.com/en/actions/quickstart)
2. [go action template](https://github.com/actions/starter-workflows/blob/main/ci/go.yml)
3. [storing artifacts](https://docs.github.com/en/actions/advanced-guides/storing-workflow-data-as-artifacts)

--- 
### Day 35: February 3, 2022

**Today's Progress**: Worked on a lot of unit tests. 

**Thoughts:** Coverage % is slowly climbing.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

none

--- 
### Day 36: February 4, 2022

**Today's Progress**: Work on Universe REST tests. 

**Thoughts:** Coverage % is slowly climbing.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

[push to other repo](https://github.com/cpina/github-action-push-to-another-repository)

--- 
### Day 37: February 5, 2022

**Today's Progress**: Built a lot of tests. Got code coverage to nearly 40%. Built a Github Action Pipeline for pushing my code coverage report to my github pages. This is a lot easier than downloading the result every time. Got sonarcloud setup as well. And fixed a lot of issues with the code.

**Thoughts:** It's really nice to see all the stuff you can do with Github Actions.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [push to other repo](https://github.com/cpina/github-action-push-to-another-repository)
2. [push example](https://github.com/cpina/push-to-another-repository-example/blob/main/.github/workflows/ci.yml)
3. [push example script](https://github.com/cpina/github-action-push-to-another-repository/blob/main/entrypoint.sh)
4. [go profiling](https://medium.com/@felipedutratine/profile-your-benchmark-with-pprof-fb7070ee1a94)
5. [github get sha](https://stackoverflow.com/questions/58886293/getting-current-branch-and-commit-hash-in-github-action)
6. [sonarqube scoppe](https://docs.sonarqube.org/latest/project-administration/narrowing-the-focus/)
7. [github push to your repo](https://github.com/ad-m/github-push-action)
8. [js script sha](https://www.w3schools.com/tags/att_script_integrity.asp)
9. [sonarqube test coverage](https://docs.sonarcloud.io/enriching/test-coverage-and-execution)
10. [golang sonarqube](https://docs.sonarqube.org/latest/analysis/languages/go/)
11. [checkout depth](https://stackoverflow.com/questions/59000099/sonarqube-with-shallow-clone-warning-even-with-shallow-disabled-on-jenkins-build?newreg=0b3a83317e0249b689a1ac764902fe66)

--- 
### Day 38: February 6, 2022

**Today's Progress**: I got sonarcloud code coverage setup so I no longer have to use github actions to save coverage reports. Built a lot of tests and got to nearly 70% code coverage. I got all the bugs, vulnerabilities, and code smells fixed in the code.

**Thoughts:** Sonarcloud is really nice.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [sonarcloud](https://sonarcloud.io/summary/overall?id=cryanbrow_eve-graphql-go)

--- 
### Day 39: February 7, 2022

**Today's Progress**: I was able to get code coverage on the overall project to 80.4%. The bare minimum that I will accept. I think I should be able to approach 90% by the time it's all done.

**Thoughts:** I've about worked off my backlog of technical debt. It will be nice to start extending the project once again.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [go vet](https://pkg.go.dev/cmd/vet)

--- 
### Day 40: February 8, 2022

**Today's Progress**: I got Jekyll installed on my github pages and setup my first blog post. I also added a few more new endpoints to the graphql server.

**Thoughts:** Having an easy to update blog is super nice.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [jekyll setup](https://dfederm.com/creating-a-blog-using-github-pages/)

--- 
### Day 41: February 9, 2022

**Today's Progress**: I installed Jaeger on my local machine. I also implemented open telemetry into one endpoint. Got it producing to Jaeger and checked out some spans.

**Thoughts:** I spent months trying to get this to work in Java and it works in minutes in Go...

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [open telemetry getting started](https://opentelemetry.io/docs/instrumentation/go/getting-started/)
2. [sampling](https://opentelemetry.io/docs/instrumentation/go/exporting_data/)
3. [jaeger impl](https://github.com/open-telemetry/opentelemetry-go/blob/main/example/jaeger/main.go)
4. [jaeger getting started](https://www.jaegertracing.io/docs/1.31/getting-started/)

--- 
### Day 42: February 10, 2022

**Today's Progress**: Got open telemetry in the entire app. Was a ton of refactoring.

**Thoughts:** My copy/paste fingers are tired. lol

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

none

--- 
### Day 43: February 11, 2022

**Today's Progress**: Built my docker image with github actions and tagged a latest and version number at the same time with multiple build types.

**Thoughts:** I'm a little lost on weather I should continue with this project to polish it up more or switch to something else to learn more.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [buildx](https://docs.docker.com/buildx/working-with-buildx/)
2. [default values](https://stackoverflow.com/questions/56049589/what-is-the-way-to-set-default-values-on-keys-in-lists-when-unmarshalling-yaml-i)
3. [default library](https://github.com/creasty/defaults)

--- 
### Day 44: February 12, 2022

**Today's Progress**: I implemented go security scanning and fixed the issues found there. I implemented a linter badge and started fixing issues that were identified by that. I updated the application to run with default settings so it can be pulled and used with zero configuration.

**Thoughts:** Working to make an application that works in multiple configuration takes a lot of thought and consideration. I do wish I new that the context should be the first field in a method before I did that huge refactor.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [godoc comments](https://go.dev/blog/godoc)
2. [GitHub Container Registry Push](https://docs.github.com/en/actions/publishing-packages/publishing-docker-images)
3. [Helm Chart GCR](https://www.visualstudiogeeks.com/github/publish-helm-3-charts-to-gcr)
4. [go report card](https://goreportcard.com/report/github.com/cryanbrow/eve-graphql-go)

--- 
### Day 45: February 13, 2022

**Today's Progress**: I implemented revive and go vet into my github actions. Got those wired into sonarcloud and reporting as code smells. Cleaned over 500 of them up. Have about 50 to go for tomorrow.

**Thoughts:** Still thinking through how to organize a large graphql schema with hundreds of queries.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [revive](https://github.com/mgechev/revive)

--- 
### Day 46: February 14, 2022

**Today's Progress**: I got all the godoc comments finished up and cleared all the code smells from revive.run. 

**Thoughts:** Still thinking through how to organize a large graphql schema with hundreds of queries.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [godocs](https://pkg.go.dev/github.com/cryanbrow/eve-graphql-go@v0.0.1)

--- 
### Day 47: February 15, 2022

**Today's Progress**: Started implementing jwt auth into the application

**Thoughts:** Still thinking through how to organize a large graphql schema with hundreds of queries.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [godocs](https://pkg.go.dev/github.com/cryanbrow/eve-graphql-go@v0.0.1)

--- 
### Day 48: February 16, 2022

**Today's Progress**: Got JWTs about 95% implemented. Just ran into an issue where a field in the JWT can be a single string or an array of strings.

**Thoughts:** Got surgery tomorrow. I hope I can keep the streak going.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [okta jwt validation](https://github.com/oktadev/okta-offline-jwt-validation-example/blob/main/main.go)
2. [parse jwt](https://pkg.go.dev/github.com/golang-jwt/jwt#example-Parse-Hmac)
3. [gqlgen interceptor](https://gqlgen.com/recipes/authentication/)
4. [eve oauth links](https://login.eveonline.com/.well-known/oauth-authorization-server)
5. [eve sso](https://docs.esi.evetech.net/docs/sso/)

--- 
### Day 49: February 17, 2022

**Today's Progress**: Got JWTs about 95% implemented. Just ran into an issue where a field in the JWT can be a single string or an array of strings.

**Thoughts:** Had surgery today. Was hard to focus.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)

**Links to references used**:

1. [file download](https://golangcode.com/download-a-file-from-a-url/)

--- 
### Day 50: February 18, 2022

**Today's Progress**: I worked on MD5 Sums on downloaded files and trying to implement redis load.

**Thoughts:** Pretty loopy from the pain meds after surgery.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

1. [golang starts with](https://stackoverflow.com/questions/12667327/go-startswithstr-string)
2. [reading file](https://gobyexample.com/reading-files)

--- 
### Day 51: February 19, 2022

**Today's Progress**: Got Agent data loaded into Redis. Started work on a few others as well.

**Thoughts:** Room is still spinning post surgery so progress is slow going.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

--- 
### Day 52: February 20, 2022

**Today's Progress**: I created models for about 10 data types. There are north of 30 total but we're making progress on loading data into Redis.

**Thoughts:** Finally feeling better post surgery.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

--- 
### Day 53: February 21, 2022

**Today's Progress**: I created models for about 6 data types. There are north of 30 total but we're making progress on loading data into Redis.

**Thoughts:** Just about full strength after the surgery.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

--- 
### Day 54: February 22, 2022

**Today's Progress**: I'm sounding like a broken record but there are a lot of data types and some of them have hundreds of fields. I'm nearing the end.

**Thoughts:** First day back to work after surgery.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

1. [git login](https://stackoverflow.com/questions/64962533/logon-failed-use-ctrl-c-to-cancel-basic-credential-prompt)

--- 
### Day 55: February 23, 2022

**Today's Progress**: Had a rough day so only accomplished a small amount today.

**Thoughts:** none

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

1. [git login](https://stackoverflow.com/questions/64962533/logon-failed-use-ctrl-c-to-cancel-basic-credential-prompt)

--- 
### Day 56: February 24, 2022

**Today's Progress**: Finished up all the types that aren't systems, constellations, and regions.

**Thoughts:** The next part is going to be a massive undertaking.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

---
### Day 57: February 25, 2022

**Today's Progress**: Started on Solar System Work.

**Thoughts:** I was right this is a huge undertaking.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

---
### Day 58: February 26, 2022

**Today's Progress**: Continued working on solar system.

**Thoughts:** The hardest part of this whole thing is going to be reconciling the two data types of the SDE and the ESI.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none

---
### Day 59: February 27, 2022

**Today's Progress**: Work on consolidating Solar System Continues

**Thoughts:** The hardest part of this whole thing is going to be reconciling the two data types of the SDE and the ESI.

**Link(s) to work**: 

* [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)
* [Eve GraphQL Helm](https://github.com/cryanbrow/eve-graphql-helm)
* [Docker for Eve GraphQL](https://hub.docker.com/repository/docker/cryanbrow/eve-graphql/general)
* [Eve SDE load](https://github.com/cryanbrow/eve-sde-redis-load)

**Links to references used**:

none