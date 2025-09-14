<sup>BD 2025</sup>

# RP/OS Sidecar for Memory
### What is it?
- Something along these lines: ![[rpos-memory-rough-sketch.jpg]]
- The above diagram is a (very) rough sketch of what this is intended to be: a public interaction management pipeline, as well as inter-protocol translation pipeline (later on), for use as one of the primary components of a decentralized social network.
- The OpenSearch (OS) DBMS stores public posts, which get uploaded through a RedPanda (RP) instance from a user's POD whenever they post a public post or have a public interaction, and also opens APIs which allow users to fetch posts directly from the client running on their devices via customized queries to the OS DBMS' API. This enables users to do things like fetch tagged posts, search for content containing key words or phrases, and fetch paginated timelines all via how the query is structured. 
- The RedPanda (RP) in-stream pipelining instance provides a means of verification of content before it's uploaded to OpenSearch as well as a means for Inter-Protocol Translation (IPT) between protocols like ActivityPub and ATProto. The IPT will be carried out by parsing the JSON object being uploaded to another server (e.g. one which represents a user liking a post on another platform in the Fediverse) and restructuring the JSON object to be in the format expected by the server on the other end.
    - Before the IPT can function as intended, the following non-inclusive list of tasks must be completed:
        - [ ] Creation of JSON schemas for use mapping components of one protocol (e.g. as:Note) to another
        - [ ] Authentication between instances running different protocols
            - May require mimicking the existence of an instance of a node for another protocol
        - [ ] Mapping of users on one protocol to (emulated) users on another
            - Ideally not by making a node of the other protocol and making user accounts on that node, but instead by essentially taking the output on our end and transforming it to the expected output on the other end such that the instance of the other protocol can't tell the difference due to our end having translated the output data to be identical to what the node of the other protocol is expecting
        - [ ] Client-side translation pipeline for Memory users who want to view content from nodes of other instances not authenticated with the node
            - No interaction would be able to take place (unless the other end put together something to interpret the user's actions), however the user would be able to view posts from other platforms, and from whatever instances of said platforms they are partial to (i.e. unrestricted access to view public posts from other instances/protocols)
            - Should be as simple as querying the instances of other protocols and asking them for whatever the user is searching for as if the user were using their protocol

