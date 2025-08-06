# Tender-to-CV Matching in IteraAI

### The Matching Process
1. Document Upload: When you upload a tender document in the tender-matching page, the system passes it to the backend through a server action.

2. **AI Analysis:** The backend processes the tender using an AI agent guided by a specialized prompt that extracts 17 standardized fields from the tender document, including:

    - Required expertise & qualifications
    - Thematic areas/sectors
    - Countries of implementation
    - Language requirements
    - Tools/methods needed
3. **Candidate Matching:** The system compares the tender requirements against CV data in the database using a weighted scoring system:

    - Thematic areas/sectors (45% weight)
    - Geographic experience (13% weight)
    - Assignment type (9% weight)
    - Donor experience (7% weight)
    - And several other factors with smaller weights
4. **Score Calculation:** Each candidate receives a total score based on how well their profile matches the tender requirements. The scoring logic applies different weights to various matching criteria and classifies candidates as:

    - Highly Relevant (85-100%)
    - Relevant (70-84%)
    - Partially Relevant (50-69%)
    - Not Relevant (<50%)

5. **Results Display:** The interface presents the matching results in two sections:

    - AI Recommended Candidates: The top candidates selected by the AI
    - Top 10 Matching Candidates: A list of candidates with top 10 match scores
    
### Key Technical Features
  - **Detailed Profiles:** You can view comprehensive candidate profiles with tabs for different information categories (overview, experience, geographic, clients, education)
  - **Score Explanation:** For each recommended candidate, the system provides a written explanation of why they match the tender
  - **Visual Indicators:** The interface uses badges and visual elements to highlight key information like years of experience, technical sectors, and match scores
  - **Real-time Processing:** The system shows progress indicators during document processing
The matching algorithm puts special emphasis on thematic alignment, ensuring that candidates with expertise in the specific areas required by the tender are prioritized, while also considering factors like geographic experience, recency of assignments, and relevant methodology expertise.

