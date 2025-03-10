# VoyageMind



# Key Technologies Used

- **ArangoDB** - To Store Graph - Nodes and Edges
- **NVIDIA cuGraph** - To run NetworkX Algorithms efficiently, on-scale
- **NetworkX** - To model the graph and run Graph Algorithms
- **OpenAI gpt-4o-mini** - As LLM
- **Langchain & Langgraph** - As Agentic Framework to Build Agentic App
- **nx-cugraph** - To run cuGraph with networkx
- **LangChain LLM Graph Transformer** - To extract Graph Entities from unstructed data

**Agentic App** uses below Agents:

1. **Data Augmentation Agent** - leverages Wikipedia to extract information about various cities as a Graph. Uses LangChain WikipediaRetriever and LLM Graph Transformer
2. **Master ReAct Agent** - Which Plans which tools to call. The ability to plan and call below tools and pass results of one to another, allows it run below queries:

* **SIMPLE QUERIES** → Dynamic AQL (via LangChain)
* **COMPLEX QUERIES** → GPU-Accelerated Graph Analytics (via NetworkX/cuGraph)
* **HYBRID QUERY EXECUTION** → Combining AQL and cuGraph for Contextual Responses

Available Tools for Master ReAct Agent:

- **Text to AQL** - Converts Natural Language to ArangoDB AQL Query
- **Text to AQL to Text** - Converts Natural Language to ArangoDB AQL Query, run it and convert the results to a Natural Language Answer
- **Text to NetworkX Algorithm** - Converts Natural Language to NetworkX Algorithm, executes it and provides response in natural Language - With Robust Re-Try Mechanism
- **NetworkX Algorithm to AQL to Text** - Converts Natural Language to NetworkX Algorithm, executes it and then passes results to execute AQL Query and then provides response in natural Language


# Key Use Cases:

## Simple Queries - Use Cases Answerable by AQL Queries

### Connectivity and Basic Path Finding
- Which cities are directly connected by flights?
- What is the shortest flight path between two specific cities?
- How many airports does each city have?

### Tourist Attraction Analysis
- Which cities have the most tourist attractions?
- What are all the tourist attractions in a specific city?
- Which cities have both airports and tourist attractions?

### Airport and Flight Statistics
- Which airports have the most incoming and outgoing flights?
- What is the total number of flights between two specific airports?
- Which cities have airports with no outgoing flights?

### Airport Connectivity Analysis
- Which airports serve as major hubs with the most connections?
- What is the average number of direct flight connections per airport?
- Which cities have airports with direct flights to the most other cities?

### Tourist Attraction Distribution
- How many tourist attractions are there per city on average?
- Which cities have the highest ratio of tourist attractions to airports?
- Are there any cities with tourist attractions but no airports?

## Complex Queries - Use Cases Requiring NetworkX Algorithms

### Complex Network Analysis
- What is the average clustering coefficient of the airport network?
- Which airports are the most central in the network based on betweenness centrality?
- What is the diameter of the flight network?

### Community Detection
- Can we identify clusters of closely connected airports?
- Are there distinct communities of cities based on their flight connections?
- How many strongly connected components exist in the flight network?

### Network Efficiency
- What is the global efficiency of the flight network?
- How does the removal of the top 5% most connected airports affect the network's efficiency?
- Which cities, if their airports were upgraded, would most improve the overall network efficiency?

## Hybrid Queries - Use Cases Requiring Both Cypher Queries and NetworkX

### Advanced Route Planning
- What is the most efficient multi-city tour covering the top 10 tourist attractions?
- Which route maximizes the number of unique tourist attractions visited within a given number of flights?
- What is the optimal flight path between two cities that includes a stopover at a city with specific tourist attractions?
- Design a 5 City Tour which covers Museums

### Comparative City Analysis
- How do cities compare in terms of their importance in the flight network versus their tourist attractions?
- Which cities serve as the best hubs for both air travel and tourism?
- What is the correlation between a city's connectivity in the flight network and its number of tourist attractions?

### Network Growth Prediction
- Based on current network structure and tourist attraction distribution, which city pairs are most likely to establish new flight routes?
- How would the addition of a new major airport in a central location affect the overall network topology and efficiency?
- Can we predict future tourist attraction development based on a city's position and growth in the flight network?

# Steps

Copy .enn.sample to .env and update it with OpenAI keys and ArangoDB credentials.
Then Open the Jupyter Notebook and follow the steps - They are self explainatory