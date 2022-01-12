# 100 Days Of Code - Log

### Day 1: December 31, 2021

**Today's Progress**: Started a golang cobra CLI for icanhazdadjoke

**Thoughts:** I completed the tutorials [Part 1](https://dev.to/divrhino/building-a-command-line-tool-with-go-and-cobra-3mjd) and [Part 2](https://dev.to/divrhino/adding-flags-to-a-command-line-tool-built-with-go-and-cobra-34f1) using cobra and golang to call the icanhazdadjoke REST API. Icanhazdadjoke has a GraphQL API, tomorrow I will converting my app to call the GraphQL implementation

**Link(s) to work**: [DadJoke CLI](https://github.com/cryanbrow/dadjoke)

--- 
### Day 2: January 1, 2022

**Today's Progress**: Added Unit tests to the dad joke CLI, mocked out the calls to the back end service.

**Thoughts:** I struggled a lot at the beginning of this. Mocking in Go is significantly more complicated than in Java with annotations. You have to create an interface for a class that already exists and then pass in a reference to the library in an init method. This init method happens before any other code execution so when you load in a Mock in your test doing the same thing it replaces what is already there. It makes sense now that I understand what's going on. It's just really quite complex for something that is rather easy in Java.

**Link(s) to work**: [DadJoke CLI](https://github.com/cryanbrow/dadjoke)

**Links to references used**:

1. [Mocking Guide](https://levelup.gitconnected.com/mocking-outbound-http-calls-in-golang-9e5a044c2555)
2. [Unit Tests](https://www.digitalocean.com/community/tutorials/how-to-write-unit-tests-in-go-using-go-test-and-the-testing-package) 

--- 
### Day 3: January 2, 2022

**Today's Progress**: Created my Eve Online graphql server from my graphql schema I had built in the past.

**Thoughts:** cqlgen is a life saver. The fact that it builds out your objects from your schema and sets up resolvers and everything. It's just incredible. The task of building resolvers is still going to be daunting for a schema the size of the one that I have but it will be fun. I don't know how unit testing for generated code works. I don't know if the best approach would be to ignore it? Feels like unit testing generated code is chasing a moving target. I'll search around tomorrow and see what people say.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [cqlgen guide](https://gqlgen.com/getting-started/)
2. [appending to slices](https://go.dev/tour/moretypes/15) 

--- 
### Day 4: January 3, 2022

**Today's Progress**: I converted my schema over to snake case and implemented the ordersForRegion resolver.

**Thoughts:** With the json implementation in the auto generated go code wanting snake case and me not wanting to modify the finals every time I built them I updated the schema. I created a resolver that only pulls the first page but that works for now. Next is caching.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [int to string](https://golang.cafe/blog/golang-int-to-string-conversion-example.html)

--- 
### Day 5: January 4, 2022

**Today's Progress**: I added a data access layer, iterated through pages, learned url.URL for building dynamic urls and struggled conditional statements.

**Thoughts:** It's really important to not overlook a != and mistake it for a ==. That cost me like 15 minutes of my life. url.URL makes calling APIs so much easier, I'm glad I took the time to do it instead of just concatenating strings.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [slice append](https://yourbasic.org/golang/append-explained/)
2. [for loop](https://yourbasic.org/golang/for-loop/)
3. [URL buildup](https://pkg.go.dev/net/url#URL)
4. [query resolvers](https://gqlgen.com/reference/resolvers/)

--- 
### Day 6: January 5, 2022

**Today's Progress**: Today was a throwaway. I implemented a resolver for systembyid but all the other work I did, did not accomplish much. ESI for EVE was down so I could test my new resolver.

**Thoughts:** The Star Wars example generates their resolvers from the schema. I really want this and for the life of me I can't figure out why mine don't. I added a couple of lines to my resolver to generate easily every time so that's nice at least.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [star wars example](https://github.com/99designs/gqlgen/tree/master/example/starwars)
2. [getting started](https://gqlgen.com/getting-started/)

--- 
### Day 7: January 6, 2022

**Today's Progress**: Figured out all of yesterdays issues and got a resolver going for the Systems within Order so that's exciting. My first nested type.

**Thoughts:** The missing piece was capitalization on my types in the schema and matching properties in the gqlgen. Also really cemented in what the parens before a method name are for. It's for defining methods for a struct with is handy. None of the Pluralsight courses I took really drove that home.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [methods](https://go.dev/tour/methods/1)
2. [eve swagger system by id](https://esi.evetech.net/ui/#/Universe/get_universe_systems_system_id)

--- 
### Day 8: January 7, 2022

**Today's Progress**: Today was just doing work. Didn't have to figure out much but accomplished an absolute ton. Got like 6-7 resolvers and dao endpoints built.

**Thoughts:** Today was just a day of doing.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [voyager](https://apis.guru/graphql-voyager/)

--- 
### Day 9: January 8, 2022

**Today's Progress**: Today was another day of just writing resolvers and endpoints into the ESI. Got a heck of a lot done though.

**Thoughts:** Today was just a day of doing. Created my first custom error though so that was fun.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [errors](https://yourbasic.org/golang/create-error/)

--- 
### Day 10: January 9, 2022

**Today's Progress**: Huge day today. I decided I wanted to increase the performance so I implemented an in memory cache for one of the API endpoints. I implemented in a way so it's agnostic to the data that is coming in which will make it super reusable.

**Thoughts:** Implemented a cache with a map to start with and ran into concurrent modification exceptions. Found sync.map and it was just what I needed. Turned out great. So now I'm caching things with expiry timestamps and everything. It's super fun.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [maps](https://medium.com/@luanrubensf/concurrent-map-access-in-go-a6a733c5ffd1)
2. [sync.map](https://pkg.go.dev/sync#Map)
3. [medium sync.map](https://medium.com/@deckarep/the-new-kid-in-town-gos-sync-map-de24a6bf7c2c)

--- 
### Day 11: January 10, 2022

**Today's Progress**: Another great day. I learned how to embed a React app in my go app so I was able to put Voyager in my app as a separate endpoint to call. I added caching to everything and I built a couple of new resolvers.

**Thoughts:** Implementing Voyager was immensely easy. In fact putting web apps in your go app is absurdly easy. Makes me think about a whole mess of helper utilities that I could put in go apps really easily.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [voyager example](https://github.com/APIs-guru/graphql-voyager/blob/master/example/index.html)
2. [embed app](https://www.fareez.info/blog/embedding-react-app-in-go-binary/) - Didn't work but if it does it's a far cleaner implementation.
3. [embed app long](https://blog.jetbrains.com/go/2021/06/09/how-to-use-go-embed-in-go-1-16/) - Worked but is a lot of code.

--- 
### Day 12: January 11, 2022

**Today's Progress**: I pulled out the REST logic into it's own method and replaced it all calls. Also did a pretty big logging overhaul. Learned how to implemented JSON fields in logs.

**Thoughts:** Really thought I broke almost everything. But managed to bring it back around. Learned why it's important to know that := is not the same as =.

**Link(s) to work**: [Eve GraphQL](https://github.com/cryanbrow/eve-graphql-go)

**Links to references used**:

1. [logrus](https://github.com/sirupsen/logrus)
2. [logging best practices](https://qvault.io/golang/golang-logging-best-practices/)