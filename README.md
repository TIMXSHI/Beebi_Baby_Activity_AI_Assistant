# About the Project
Inspiration
As new parents, we recognized how overwhelming it can be to understand and monitor a newborn's patterns—especially when you're busy managing sleep, feeds, and diapers. While existing baby tracking apps often rely on charts and summary cards, they still require parents to interpret the data themselves and do their own analysis. We found this approach lacking in efficiency and clarity, particularly for exhausted new parents. That’s why we created Beebi, an Android app designed to go beyond static reports. Our goal is to transform raw baby activity logs into actionable insights, using AI agents to make data-driven parenting both simpler and more intuitive.

What it does
Beebi empowers parents to log daily baby care activities—sleep, feedings, diaper changes, and more—and receive AI-generated insights in real-time. Through an integrated chatbot powered by Google’s ADK and LLMs, parents can ask questions like “is everything good of my baby feed for past two weeks?” or “how's my baby diaper, any abnormal for the past month?” and get smart, conversational answers. Instead of digging through charts, users get direct, contextual responses that help them better understand their baby's development.

Parents can also ask general questions like “how's my baby's sleep, diaper and feed pattern for the past 15 days, can give me a comprehensive report?”—and the AI agent will generate a comprehensive, section-by-section summary, along with personalized insights and any areas of concern or suggested improvements.

For example:
_“Over the past 7 days, Kai has averaged 14.2 hours of sleep per day, with improving overnight consistency. Daytime naps are becoming shorter but more structured. Feeding volume has increased by 15%, especially in the afternoon sessions, indicating healthy growth. Diaper frequency is stable, with a healthy ratio of wet and dirty diapers.

However, Kai's overnight wake-ups have slightly increased in the past three days, which may be worth monitoring. Additionally, the last two days show a drop in morning feeding volume—this could be due to cluster feeding in the evenings, but should be observed to ensure it's not a sign of reduced appetite.”_

By highlighting both strengths and potential issues, Beebi helps parents not only reflect on past behavior but also proactively respond to early signals, making it a smart and supportive co-pilot in the parenting journey.



Since the core of this project is built on Google's Agent Developer Kit (ADK), this repository only includes backend logic and agent orchestration—it does not contain any frontend interface code.

To test the functionality of the system, we provide two recommended methods:
#### Local run with ADK:
Use the command ```adk web ``` followed by ```adk run beebi ``` to launch the ADK runtime and serve the Beebi agent locally.

#### AdkApp Testing:
Instantiate and interact with the agent programmatically via the AdkApp class for scripted or automated testing scenarios.

## Architecture Diagram
![original](https://github.com/user-attachments/assets/fa87c310-fb4c-47ff-bc9a-3f63bb14174c)

### ADK FrameWork
![Editor _ Mermaid Chart-2025-06-22-170041](https://github.com/user-attachments/assets/e375e110-51fb-4294-8a4a-507ebcdc421b)

### User Interface Demo
![screenshot1](https://github.com/user-attachments/assets/be4eab67-2803-4dfb-93e6-12c940ca3a0d)
![screenshot2](https://github.com/user-attachments/assets/32fabc43-ffcd-4943-9c56-234e2d45cc0f)


## Technology Stack

### Database Layer
[![Azure SQL](https://img.shields.io/badge/Microsoft%20Azure%20SQL-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/en-us/products/azure-sql/)
- Azure SQL Server
- Azure SQL Database
- Stores structured baby care event data

### AI Agent Layer
[![Google Gemini](https://img.shields.io/badge/Gemini-4285F4?style=for-the-badge&logo=googleai&logoColor=white)](https://deepmind.google/technologies/gemini/)
[![Google ADK](https://img.shields.io/badge/Google%20ADK-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://google.github.io/adk-docs/)
[![Cloud Google Run](https://img.shields.io/badge/Google%20Cloud%20Run-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com/run)
[![Google Vertex AI](https://img.shields.io/badge/Google%20Vertex%20AI-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com/vertex-ai)
- Gemini LLM with Google AI SDK for generating personalized insights
- Google ADK for building and orchestrating multi-agent AI architecture
- SubAgents:
  - Sleep Monitoring
  - Feeding Analysis
  - Diaper Change Tracking
  - Health Reporting
- Root Agent hosted on Cloud Run (deployment in process)
- Genetic insight summaries

### Mobile App Layer
[![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://developer.android.com/)
[![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.java.com/)
- Native Android Application (Java/Kotlin)
- User input processing
- Response visualization

### Backend Layer
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
- Node.js + Express for the backend server
- FastAPI to connect frontend with backend and AI services
- Parameter transformation
- Tool function routing

### Deployment
[![Cloud Run](https://img.shields.io/badge/Google%20Cloud%20Run-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com/run)
- Google Cloud Run for deploying the AI agent system

## Data Flow
1. **User Input**: Android app captures user requests
2. **Middleware**: Cloud Run endpoint processes requests
3. **AI Processing**:
   - Root Agent orchestrates subagents
   - Gemini LLM generates insights
4. **Data Persistence**:
   - Azure SQL stores interaction data
   - Azure SQL transmit basic data to AI agnet layer
6. **Response Delivery**: Processed results returned to mobile app

## Key Features
- Google ADK Multi-agent AI architecture with 4 specialized subagents
- Context-aware parameter transformation
- User data integration via Azure SQL
- Google Cloud Run deployment

## Deployment
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com)
[![Azure](https://img.shields.io/badge/Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com)


# Local run with ADK
## Installation
1. Clone the repo
```bash
git clone https://github.com/danielwang2025/beebi_ADK 
```
2. Setup Environment
```bash
# Create virtual environment in the root directory
python -m venv venv
# macOS/Linux:
source .venv/bin/activate
```
## Install dependencies
```bash
pip install -r requirements.txt
```
## Run the project
```bash
adk run beebi_AdkWeb
or
cd beebi_AdkWeb
adk web
```

# Programmatic agent testing(inlcuding deployment Code)

#### 1. Enable Vertex AI API
#### 2. Need a service account with Vertex AI + Agent Engine access (Set up service account credentials)
#### 3. Set your active project ID    gcloud config set project [YOUR_PROJECT_ID]
#### 4. Install dependencies/requirements.txt
#### 5. ``` cd beebi_AdkApp python agent.py ```

## Contact

Daniel(Zhichong) Wang - [Github](https://github.com/danielwang2025)  
Tim Shi - [Github](https://github.com/TIMXSHI)  

## Contributors

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/danielwang2025">
        <img src="https://avatars.githubusercontent.com/u/125905701?v=4" width="80px;" style="border-radius: 50%;" alt="Daniel(Zhichong) Wang"/><br/>
        <sub><b>Daniel(Zhichong) Wang</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/TIMXSHI">
        <img src="https://avatars.githubusercontent.com/u/130257899?v=4" width="80px;" style="border-radius: 50%;" alt="Tim(Yaozhong) Shi"/><br/>
        <sub><b>Tim(Yaozhong) Shi</b></sub>
      </a>
    </td>
  </tr>
</table>



# Acknowledgments
This project is submitted to [![Devpost][devpost]][devpost-url] as part of a hackathon project for the Agent Development Kit Hackathon with Google Cloud.

[devpost]: https://img.shields.io/badge/Devpost-003E54?style=for-the-badge&logo=Devpost&logoColor=white
[devpost-url]: https://googlecloudmultiagents.devpost.com/?ref_feature=challenge&ref_medium=discover&_gl=1*yi86ui*_gcl_au*MTE3ODA4Njc5Ni4xNzUwNDcwNzUz*_ga*MzY4MDAwNTk4LjE3NTA0NzA3NTM.*_ga_0YHJK3Y10M*czE3NTA0NzA3NTIkbzEkZzEkdDE3NTA0NzI0MDgkajQ5JGwwJGgw
