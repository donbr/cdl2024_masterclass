# Connected Data London 2024 - ERKG masterclass

How to create knowledge graphs from structured and unstructured data
based on entity resolution, to enhance downstream AI applications.


## Abstract

Graph RAG has become a buzzword in the tech industry recently, given
the popularity of using knowledges graphs to "ground" LLMs with
domain-specific facts. This approach improves the overall quality of
responses in AI applications by reducing "hallucination" in the
results. It also allows for faster data updates and helps reduce the
need (and costs) for fine-tuning LLM models.

While most Graph RAG examples tend to use LLMs to generate graph
elements automatically, we'll step back and examine the workflows
needed for generating knowledge graphs from structured and
unstructured data sources. By employing state-of-the-art open models
and open source libraries at each step, in this masterclass we will
explore how to combine the use of entity resolution and entity linking
to produce graphs that emphasize data quality, curation, and feedback
from domain experts, while making affordances for audits,
evidence-based decision making, and practices required for
mission-critical enterprise applications in highly-regulated
environments.

Overall, we will discuss a generalized architecture for how to build
and update knowledge graphs using a blend of structured and
unstructured data sources, and consider the impact of entity
resolution on downstream AI apps.


Target audience: data science teams, people with general interest in AI -- especially in highly-regulated enterprise environments.

Level: intermediate

Prerequisite Knowledge: some experience coding in Python and familiarity with popular packages such as Pandas and Jupyter.


## Key Topics

  * Distinguish among the key terminology: entity resolution, named entity recognition, relation extraction, entity linking.
  * Leverage entity resolution to provide a semantic overlay on records from structured data, i.e., generating graph elements while preserving evidence.
  * Using a textgraph algorithm to construct a lexical graph alongside the text chunking and embedding needed for retrieval augmented generation (RAG).
  * Graph construction practices which are consistent with the needs of trustworthy AI applications, audits, evidence-based decision making, and so on.
  * Case studies for production use cases which leverage these practices.
  * Why not simply use an LLM to do all of the work?


## Goals

  1. Gain hands-on experience creating knowledge graphs from both structured sources and unstructured sources, for use in a Graph RAG application.
  2. Follow practices which emphasize data quality plus affordances for audits, evidence handling, and trustworthy AI applications downstream.
  3. Use entity resolution to create the "backbone" of a knowledge graph from structured data sources.
  4. Compare use of contemporary state-of-the-art open models and open source libraries in Python for extracting graph elements from unstructured data sources.
  5. Use entity resolution results to build a context-sensitive entity linker, blending graph elements from structured and unstructured sources.


## Session outline:

  * Start with multiple open datasets used in sanctions compliance (e.g., money laundering, ultimate beneficial ownership, and relate work) as structured data sources.
  * Use entity resolution to identify entities and relations which have supporting evidence (e.g., for use in investigations).
  * Build a "skeleton" graph from the structured data sources plus the "semantic overlay" of entities and relations.
  * Load unstructured data (e.g., from relevant news articles) and split into text chunks organized in a vector database, based on an embedding model.
  * Parse the text chunks to build a lexical graph, then use a textgraph algorithm to extract its most important elements.
  * Build a context-specific entity linker based on the entity resolution results from above, to blend the unstructured elements into the "skeleton" graph.
  * Show how to use the resulting knowledge graph and vector database together in a Graph RAG application.


## Format

This class will start with a lecture describing important terms and
practices, then move to hands-on coding examples in Python.  We'll
work with a collection of Jupyter notebooks which are available in
this GitHub repository.

Each notebook illustrates an important section of code, along with
information for debugging, illustrating intermediate results, and
performance monitoring.

Then we'll work with a Python program which assembles these pieces
into one application, which you can repurpose for your own use cases.

To make the most of the time available (2 hours) we will link to some
other online tutorials for deep-dives into specific areas which are
beyond the scope of this class.


---


## General Background

> Defenders think in terms of lists, while attackers think in graphs; the latter prevail – paraphrasing from [John Lambert](https://github.com/JohnLaTwC/Shared/blob/master/Defenders%20think%20in%20lists.%20Attackers%20think%20in%20graphs.%20As%20long%20as%20this%20is%20true%2C%20attackers%20win.md)

In this masterclass, we'll how portions from six open source tutorials. Overall, these illustrate a process for using _entity resolution_ as a basis for blending elements from structured and unstructure data into constructing knowledge graphs used for GraphRAG and other AI apps downstream.
Each of these tutorials has associated articles, code repositories, slide decks, and videos. In general, the main concepts were described in
["Unbundling the Graph in GraphRAG"](https://www.oreilly.com/radar/unbundling-the-graph-in-graphrag/).


### Senzing ER Playground, with open data

This initial set of tutorials shows the basics for how to use _entity resolution_ (ER) to merge datasets, which generates graph elements:

Follow the instructions for the [Senzing ER playground](https://senzing.dockter.com/files/presentations/jupyter-sandbox.mp4), developed by Michael Dockter:
<https://github.com/senzing-garage/playground>

```bash
docker run -it --name senzing-playground -p 8260:8260 -p 8261:8261 --rm senzing/playground
```

Once this is downloaded and running, then we'll run ER to merge [three small datasets](https://www.youtube.com/watch?v=mY55S6a9Iok) together:
<http://localhost:8260/jupyter/lab/tree/python/senzing_load_truthsets.ipynb>

  * explore the `customers`, `reference`, `watchlist` datasets
  * inspect the `"Robert Smith"` entity
  * note how ER generates graph elements: entities, relations, properties

Next we'll work with open data for tracking sanctioned organizations and _ultimate beneficial ownership_ connections:
<http://localhost:8260/jupyter/lab/tree/python/senzing_load_user_data.ipynb>

  * load datasets from <https://github.com/Kineviz/senzing_starter_kit>
  * show the merge of [OpenSanctions](https://www.opensanctions.org/) and [Open Ownership](https://www.openownership.org/en/)
  * inspect the `"Abassin Badshah"` entity
  * compare with the related graph visualization: <https://derwen.ai/s/khj9#43>


### ERKG tutorial

This next section explores how to create knowledge graphs based on entity resolution using structured data sources.
Based on the article ["Entity Resolved Knowledge Graphs: A Tutorial"](https://neo4j.com/developer-blog/entity-resolved-knowledge-graphs/), the first part loads data from three sources about businesses in the Las Vegas metro area.
Merging these datasets using ER, we'll visualize potential [PPP loan fraud](https://www.justice.gov/usao-nv/pr/nevada-man-convicted-112-million-covid-19-fraud) during the pandemic.

Given our time constraints, we won't re-run this code.
Instead we will explore some Jupyter notebooks which show the execution step-by-step and the results:
<https://github.com/DerwenAI/ERKG/tree/main/examples>

The second part (by Clair Sullivan) is described in the article ["When GraphRAG Goes Bad: A Study in Why you Cannot Afford to Ignore Entity Resolution"](https://www.linkedin.com/pulse/when-graphrag-goesbad-study-why-you-cannot-afford-ignore-sullivan-7ymnc/).
Clair adds _GraphRAG_ to the Las Vegas PPP tutorial using [LangChaing](https://www.langchain.com/) to produce a chatbot for exploring potential fraud.
The execution time would be much longer than our class, so instead we'll review results in:
<https://github.com/cj2001/erkg_demo>


### Constructing KGs from Unstructured Data

Next, let's explore how to [unbundle KG construction](https://derwen.ai/s/khj9#19) based on unstructured data, instead of simply throwing all the data at an LLM!

  - code: <https://github.com/DerwenAI/strwythura>
  - video: <https://youtu.be/B6_NfvQL-BE>
  - slides: <https://derwen.ai/s/2njz#1>

Following the instructions in the `README.md` we'll run these notebooks:

  * `construct.ipynb` -- detailed KG construction using a lexical graph
  * `chunk.ipynb` -- simple example of how to scrape and chunk text
  * `vector.ipynb` -- query LanceDB table for text chunk embeddings (after having run `demo.py`)
  * `embed.ipynb` -- query the entity embedding model (after having run `demo.py`)


### Entity Linking

In this last section, we'll show how to use ER results to train an _entity linker_ to blend structured and unstructured graph elements.
This part ties the other sections together into a whole picture.

The process was developed by Louis Guitton, and described in the article ["Panama Papers Investigation using Entity Resolution and Entity Linking"](https://guitton.co/posts/entity-resolution-entity-linking).
This employes a `spaCy` pipeline component [`spacy-lancedb-linker`](https://github.com/louisguitton/spacy-lancedb-linker] which is available for [download from PyPi](https://pypi.org/project/spacy-lancedb-linker/).
The tutorial is available in:
<https://github.com/louisguitton/erkg-tutorials>

In the interest of time, we won't be able to run all of this code, so instead we'll review the results in:
<https://github.com/louisguitton/erkg-tutorials/blob/main/tutorial.ipynb>

