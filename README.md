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

## Set up


