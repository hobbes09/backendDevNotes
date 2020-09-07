# What to talk about

1. Brief introduction about the Service
2. For each project :
  * Mention the objective in 1 line
  * What was your role
  * How was the project accomplished (Planning and technical)
  * Technical challenge aspect
  * How did you overcome it
  * What were the other approaches considered and their pros and cons
  * Comment about overall scale / resiliency / availability and how it was overcome
  * Any particular debugging case


# Hotstar

## Video Playback

### About
1. Authorization (Active and reactive)
  - Location based
  - Subscription based
  - Rate limiter based
  - Risk appetite (Reactive)

2. Playback distribution
  - Playback Fetch
  - Tokenization

#### Technical challenging aspect
1. High scale handling capability
  - Service has both sync and async operations
  - Async operations : Rate limiters, Risk analysis
  - Orthogonality of the language : For redis in Java (Jedis/Lettuce/Reddison), in Golang OOTB

  (Jedis [Not thread safe] = Sync + Pipelines)
  (Lettuce [Multi-threaded and event based] = sync (async underneath) + async + reactive + pipeline)
  (Jedis Multi-threaded via JedisPool)
  (redis.Client is thread-safe, but NOT redis.Multi, redis.Pipeline and redis.PubSub. Use pools of connections if required)

2. Rate Limiter multiple types
  - Redis cluster doesnt support multi-get or pipeline
  - Configure :
  (Cluster - min and max connections used by goroutines / Context switching / latency)
  (Maximize engine utilisation / Less context switching between connections)
  (strategy of update/retrieval for minimal interaction)
  (Separate Master slave connections)
  (Use circuit breakers)
  (Degradation policies)

3. Change rate limiter policies without deployment
  - Config change in file
  - Mention other approaches considered
4. Playback tokenization for different CDNs and on-the-fly validity
5. Detailing introduced for easy debugging of outdated tokens for free content served from CDN


## UM - IPL preparation

### About
- UM
- Concurrency
- Communication
- Playback

### To do

- Prepare load environment
- Analyzing user behaviors from previous games
- Estimating the behavior in next event
- Estimate max load per Service
- Estimate load distribution for critical APIs based on user journeys
- Estimate the peak requirements of different infrastructure and downstream services and vendors
- Create ladder for scaling based + Auto-scaling
- Define degradation policies for each dependencies in each service
- Create panic handler for each service
- Disaster recovery strategy
- Verify all alarms systems are working fine
- Vertical testing of each service - results in per pod estimation and checking of degraded performance and efficient utilization of resources, and panic verification
- Gameday scripts to mock the real-match traffic volume



## Communication Service

### Technical challenges

- Initial architecture
- Mysql as a constrains
- Eventual consistent report data
- Ordering and acknowledgement discussion in kafka
- Vendor latency issue
- Adjustable weight distribution
- Adjustment on vendor side incase of latency
- Panic handler for Vendor and service
- What other approaches can be taken : (OTP by owner email / Other login methods)


# To read later

https://docs.keydb.dev/blog/2019/10/07/blog-post/

https://github.com/JohnSully/KeyDB

https://medium.com/@john_63123/redis-should-be-multi-threaded-e28319cab744
