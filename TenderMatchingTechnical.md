# Tender-to-CV Matching in IteraAI

### The Matching Process

1. **Document Upload:**  
   When a tender document is uploaded, the system initiates a backend pipeline to begin analysis.

2. **Document Parsing:**  
   The document is parsed using PDF.js or a similar library, preserving the structure and extracting the raw text.

3. **AI-Powered Extraction:**  
   Parsed content is sent to the Gemini API, where a specialized prompt extracts structured data in JSON format with 17 standardized fields, including:

   - Required expertise and qualifications  
   - Thematic areas/sectors  
   - Country and geographic implementation focus  
   - Language requirements  
   - Methodologies, tools, or donor-specific expectations  

4. **Candidate Matching:**  
   Tender data is compared against CV profiles stored in the database through a multi-stage matching process:

   - **Vector Embeddings:**  
     Both tender fields and CV attributes are converted into vector embeddings using AI models. Semantic similarity allows concept-level matches (e.g., “climate change” ≈ “environmental sustainability”).

   - **Weighted Field Comparison:**  
     A weighted scoring system compares different fields between tender and CVs. Example:
     ```js
     const weightedScore =
         thematicMatch * 0.45 +
         geographicMatch * 0.13 +
         assignmentTypeMatch * 0.09 +
         donorMatch * 0.07;
     // Additional weighted fields...
     ```

   - **Recency Boosting:**  
     Recent experiences are prioritized using a time decay function that reduces the weight of older assignments.

   - **Threshold Filtering:**  
     Candidates scoring below specific thresholds are filtered or categorized:
     - Highly Relevant: 85–100%  
     - Relevant: 70–84%  
     - Partially Relevant: 50–69%  
     - Not Relevant: <50%  

5. **Score Calculation & Result Display:**  
   The system calculates and normalizes total scores to a 0–100% scale. It then displays:

   - **AI Recommended Candidates:** Top 3–5 candidates based on relevance  
   - **Top 10 Matching Candidates:** A broader view of strong contenders  

---

### Key Technical Features

- **Detailed Profiles:**  
  Each candidate profile includes tabs for overview, experience, geographic coverage, clients/donors, and education.

- **Score Explanation:**  
  AI-generated rationale explains why a candidate is a strong match, turning numbers into clear, human-readable reasoning.

- **Visual Indicators:**  
  Badges and design elements highlight match scores, key expertise areas, years of experience, and sectors.

- **Async & Cached Processing:**  
  Matching runs asynchronously with real-time progress indicators. Tender data is cached and CV embeddings are pre-computed for performance optimization.

---

The entire system emphasizes **semantic understanding**, **contextual relevance**, and **domain-specific weighting**, going far beyond keyword matching to find the most qualified candidates for each tender opportunity.
