# SHL

Srep 1: Data Scraping
why did I take these decisions
1. choosing the libraries that I did? Beautiful soup and playwrite.
2. Are there any other alternatives
3. what steps did I do?
4. how many parts it was divided into? 2
5. which tag did I find in the catalog page that had all the dtails
6. So did I just looked inside the tag or the tr, and why?


$env:GROQ_API_KEY="your_api_key_here"
py -m uvicorn main:app --reload
http://127.0.0.1:8000/docs

"""
SHL Assessment Recommender — main service
==========================================
Pipeline stages (in order):
  1. FastAPI + Pydantic input validation
  2. Turn counter guard
  3. Stateless reconstruction from messages[]
  4. Single merged LLM call  (context extraction + intent + sufficiency)
  5. Scope guard              (off-topic / legal / prompt-injection → refuse)
  6. Hybrid retrieval         (BM25 + FAISS + RRF, no hard cutoff)
  7. Rank-based selection     (top-K by rank, LLM trims to ≤10)
  8. Structured catalog fields injected for compare / recommend
  9. LLM response generator   (Groq Llama 3, system prompt + catalog context)
 10. URL validation guard     (strip anything not in catalog allowlist)
 11. EOC logic                (explicit three-rule criteria)
 12. Pydantic output guard    (coerce + validate before returning)

Compatible with future stages: scraper, evaluation harness, refinement loop.
"""
