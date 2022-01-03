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

**Links to tutorials followed**:

1. [Mocking Guide](https://levelup.gitconnected.com/mocking-outbound-http-calls-in-golang-9e5a044c2555)
2. [Unit Tests](https://www.digitalocean.com/community/tutorials/how-to-write-unit-tests-in-go-using-go-test-and-the-testing-package) 

--- 
### Day 3: January 2, 2022

**Today's Progress**: Created my Eve Online graphql server from my graphql schema I had built in the past.

**Thoughts:** cqlgen is a life saver. The fact that it builds out your objects from your schema and sets up resolvers and everything. It's just incredible. The task of building resolvers is still going to be daunting for a schema the size of the one that I have but it will be fun. I don't know how unit testing for generated code works. I don't know if the best approach would be to ignore it? Feels like unit testing generated code is chasing a moving target. I'll search around tomorrow and see what people say.

**Link(s) to work**: [DadJoke CLI](https://github.com/cryanbrow/eve-graphql-go)

**Links to tutorials followed**:

1. [cqlgen guide](https://gqlgen.com/getting-started/)
2. [appending to slices](https://go.dev/tour/moretypes/15) 