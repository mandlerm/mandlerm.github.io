# Latency and Bandwidth

The longer I trek along my Software Engineering journey, the more I appreciate building a solid mental model of the concepts I am learning. Finding tips and tricks to cement concepts in my brain in a way that is memorable for me is a daily challenge - and a welcomed one.  Most recently, such a mental model was created for understanding Latency and Bandwidth.

At a high level, _latency_ refers to **speed** and _bandwidth_ refers to **capacity**. I think of this in terms of a car driving on a road.

Assuming that the speed limit is actually followed, _latency_ is determined by the speed limit on a road. That speed limit indicates how fast the the car (or data) can travel. It's a maximum speed limit, and various things may cause the actual speed to be lower than the potential speed - which we will get to in a moment.

_Bandwidth_ is impacted by the number of lanes on our imaginary road.  The more lanes, the more cars can travel at the same time.  Just as with road systems, different connections will have a different bandwidth.  

You may cruise along a four-lane Interstate for a while, but eventually you will exit and may end up on a single lane road.  The bandwidth for the transportation of data is similar. Different segments/connections may have different bandwidths.

### Let's head back to latency.

There are multiple catagories of latency - let's look at each one.

#### Propagation Delay
This is the speed limit on any particular road. It will take a certain amount of time to get from sender to receiver - a ratio of distance to speed.  If you are hand delivering a message to Grandma's house and she lives down the road a few miles, the time it takes you go get there is considered the **propagation delay**.

#### Transmission Delay
But traveling to Grandma isn't as easy as driving down the road.  She's a number of roads away, which require one highway interchange, a traffic circle, and a number of left hand turns.  Each time you head through an intersection you will experience **transmission delay**.

#### Processing Delay
But Grandma lives over the river and through the woods, so your Mustang convertable is not going to cut it for the entire journey.  You channel your inner [Inspector Gadget](https://www.youtube.com/watch?v=e-JHfXVlkik) and transform your smooth ride first into a canoe and then into a carriage (work with me here!).  This one may be a bit of a stretch, but the point is that sometimes the data needs to be processed as it changes links along the route, and this too causes delay.

#### Queuing Delay
After getting through the [Fire Swamp](https://www.youtube.com/watch?v=syKsWfqWUqk) you hop onto the Jersey Turnpike and get stuck in a queue as you line up to pay the toll. Only one car can pass at a time, causing a buffer.

#### Last-Mile Latency 
Finally you get off the Turnpike and make the 52 short turns to get off of the main road and into Grandmas' neighborhood, on to her street and eventually into her driveway.  All of the small hops take additional time and that last mile took a crazy amount of time considering the short distance.

#### Round Trip Time
You've finally arrived but Grandma is an active lady! You barely knock on her door and hand her the message before she says, "Thanks for the card, but I'm heading out to play Bridge at my Senior Center."  Quick as a wink, Grandma is gone, so you hop back in your car and return home -- maybe taking the same route, maybe not. Eventually you arrive home and announce, 'Grandma got the message'.  This is your RTT.  

**Congratulations!**
